<template>
  <div class="w-[90%]">
    <table class="text-center text-white w-full">
        <thead class="bg-primary">
            <th>No</th>
            <th>Barcode</th>
            <th>Item</th>
            <th>Harga</th>
        </thead>
        <tbody>
            <tr v-for="(item,i) in items" :key="i" :class="[i % 2 == 0 ? 'bg-gray-400': 'bg-gray-500']" class="hover:opacity-90" @click="itemClick(item)">
                <td class="py-3">{{i+1}}</td>
                <td>{{item.barcode}}</td>
                <td>{{item.nama}}</td>
                <td><span class="bg-green-600 p-2 rounded-md">{{item.harga}}</span></td>
            </tr>
        </tbody>
    </table>
  </div>
</template>

<script>
export default {
    name:'Table-Comp',
    props:{
        items:String
    },
    methods:{
        itemClick(item){
            this.$router.push(`/item/${item.id}`)
        }
    }
}
</script>

<style>

</style>