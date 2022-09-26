<template>
  <div class="flex flex-col items-center gap-5">
    <div class="mt-5 border-primary border-2 rounded-md">
        <Input placeholder="nama barang" @isInput="onInput"/>
        <Button name="Cari"/>
    </div>
    <Table :items="data"/>

    <Button class="w-[90%]" name="Tambah Barang" @isClick="addClick"/>
  </div>
</template>

<script>
import Button from '@/components/Button.vue'
import Input from '@/components/Input.vue'
import Table from '@/components/Table.vue'

export default {
    name:'Home-View',
    components:{
        Button,Input,Table
    },
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
            data:[]
        }
    },
    methods:{
        onInput(value){
            const getItems = this.getName(value)
            this.data = getItems
        },
        getName(value){
            const items = []
            this.items.forEach(item => {
                if (item.nama.toLowerCase().startsWith(value)){
                    items.push(item)
                }
            })
            return items
        },
        addClick(){
            this.$router.push('/add')
        }
    },
    created(){
        this.data = this.items
    }
}
</script>

<style>

</style>