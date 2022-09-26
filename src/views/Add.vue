<template>
  <div class="w-full flex flex-col items-center gap-3">
    <Input class="border-primary border-2 w-[90%] rounded-md h-10 mt-20" placeholder="barcode"/>
    <Input class="border-primary border-2 w-[90%] rounded-md h-10" placeholder="nama"/>
    <Input class="border-primary border-2 w-[90%] rounded-md h-10" placeholder="harga"/>
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
            this.$router.push('/')
            console.log('kembali')
        },
        addClick(){
            console.log('add')
        }
    }
}
</script>

<style>

</style>