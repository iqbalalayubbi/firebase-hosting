<template>
    <div class="w-full flex flex-col items-center gap-3">
        <Input :value="barcode" class="border-primary border-2 w-[90%] rounded-md h-10 mt-20" placeholder="barcode"/>
        <Input :value="nama" class="border-primary border-2 w-[90%] rounded-md h-10" placeholder="nama"/>
        <Input :value="harga" class="border-primary border-2 w-[90%] rounded-md h-10" placeholder="harga"/>
    <Button name="Simpan" class="w-[90%]" @isClick="addClick"/>
    <Button name="Delete" class="w-[90%] bg-red-500" @isClick="addClick"/>
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
        backClick(){
            this.$router.push('/')
        }
    },
    created(){
        this.items.forEach(item => {
            if (item.id == this.$route.params.id){
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