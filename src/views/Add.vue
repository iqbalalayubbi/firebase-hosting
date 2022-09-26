<template>
  <div class="w-full flex flex-col items-center gap-3">
    <Input ref="barcode" class="border-primary border-2 w-[90%] rounded-md h-10 mt-20" placeholder="barcode"/>
    <Input ref="nama" class="border-primary border-2 w-[90%] rounded-md h-10" placeholder="nama"/>
    <Input ref="harga" class="border-primary border-2 w-[90%] rounded-md h-10" placeholder="harga"/>
    <Button name="Tambah" class="w-[90%]" @isClick="addClick"/>
    <Button name="Kembali" class="w-[90%] bg-red-500" @isClick="backClick"/>
  </div>
</template>

<script>
import Input from '@/components/Input.vue'
import Button from '@/components/Button.vue'

export default {
    name:'Add-View',    
    components:{
        Input,Button
    },
    methods:{
        backClick(){
            this.$router.push('/home')
            console.log('kembali')
        },
        addClick(){
            function rand(digit){
                const str = []
                for(let i =0; i < digit;i++){
                    str.push(Math.floor(Math.random()*9))
                }
                return str.join('')
            }
            const ref = this.$refs
            const item = {
                id : rand(9),
                barcode : ref.barcode.$refs.input.value,
                nama : ref.nama.$refs.input.value,
                harga : ref.harga.$refs.input.value,
            }
            const items = JSON.parse(localStorage.getItem('items'))
            items.push(item);
            localStorage.setItem('items',JSON.stringify(items))
            this.$router.push('/home')
        }
    },
}
</script>

<style>

</style>