<template>
    <div class="w-full flex flex-col items-center gap-3">
    <div class="mt-20 w-[90%] flex flex-col">
        <label for="">Barcode</label>
        <Input ref="barcode" :value="barcode" class="border-primary text-gray-600 border-2  rounded-md h-10 " placeholder="barcode"/>
    </div>
    <div class="w-[90%] flex flex-col">
        <label for="">Nama</label>
        <Input ref="nama" :value="nama" class="border-primary text-gray-600 border-2 rounded-md h-10" placeholder="nama"/>
    
    </div>
    <div class="w-[90%] flex flex-col">
        <label for="">Harga</label>
        <Input ref="harga" :value="harga" class="border-primary text-gray-600 border-2 rounded-md h-10" placeholder="harga"/>
    
    </div>
    <Button name="Simpan" class="w-[90%]" @isClick="updateClick"/>
    <Button name="Delete" class="w-[90%] bg-red-500" @isClick="delClick"/>
    <Button name="Kembali" class="w-[90%] bg-gray-500" @isClick="backClick"/>
  </div>
</template>

<script>
import Input from '@/components/Input.vue'
import Button from '@/components/Button.vue'

export default {
    name:'Item-View',
    components:{Input,Button},
    data(){
        return{
            items:[
                    {id:'1',barcode:'2940839090',nama:'sosis sonice',harga:1000},
                    {id:'2',barcode:'5445546565',nama:'real good',harga:4000},
                    {id:'3',barcode:'5445546565',nama:'susu beruang',harga:4000},
                    {id:'4',barcode:'3843843843',nama:'nabati',harga:6000},
                    {id:'5',barcode:'9359590595',nama:'beras',harga:11000},
                    {id:'6',barcode:'3204293943',nama:'good day',harga:7000}
                ],
            barcode:'',
            nama:'',
            harga:'',

        }
    },
    methods:{
        updateClick(){
            const id = this.$route.params.id
            const ref = this.$refs
            const newItem = {
                id,
                barcode : ref.barcode.$refs.input.value,
                nama : ref.nama.$refs.input.value,
                harga : ref.harga.$refs.input.value,
            }
            const items = JSON.parse(localStorage.getItem('items'))
            items.forEach((item,i) => {
                if (item.id == id){
                    items.splice(i,1,newItem)
                    localStorage.setItem('items',JSON.stringify(items))
                }
            })
            this.$router.push('/home')
        },
        delClick(){
            const id = this.$route.params.id
            const items = JSON.parse(localStorage.getItem('items'))
            console.log(items)
            items.forEach((item,i) => {
                if (item.id == id){
                    items.splice(i,1)
                }
            })
            fetch('http://localhost:3000/items/'+id,{
                method:'delete',
            }).then(res => res.json()).then(() => {
                localStorage.setItem('items',JSON.stringify(items))
                this.$router.push('/home')
            })
        },
        backClick(){
            this.$router.push('/home')
        }
    },
    async created(){
        const id = this.$route.params.id
        const items = JSON.parse(localStorage.getItem('items'))
        items.forEach(item => {
            if (item.id == id){
                this.barcode = item.barcode
                this.nama = item.nama
                this.harga = item.harga
            }
        })
    }
}
</script>

<style>

</style>