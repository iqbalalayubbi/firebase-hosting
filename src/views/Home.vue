<template>
  <div class="flex flex-col items-center gap-5">
    <h1 class="font-bold mt-10 text-4xl">KIOS SULTON</h1>
    <div class=" mb-3 w-[90%] border-primary border-2 rounded-md">
        <Input placeholder="nama barang" @isInput="onInput" class="h-10"/>
    </div>
    <Table :items="data"/>

    <Button class="w-[90%]" name="Tambah Barang" @isClick="addClick"/>
    <Button class="w-[90%] bg-red-500" name="Logout" @isClick="outClick"/>
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
            items:[],
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
        },
        outClick(){
            fetch('http://localhost:3000/items',{
                method:'post',
                headers:{
                    'Content-Type':'application/json'
                },
                body:localStorage.getItem('items')
            }).then(res => res.json()).then(() => {
                localStorage.removeItem('items')
                this.$router.push('/')
            })
        }
    },
    created(){
        this.data = JSON.parse(localStorage.getItem('items'))
        this.items = JSON.parse(localStorage.getItem('items'))      
    }
}
</script>

<style>

</style>