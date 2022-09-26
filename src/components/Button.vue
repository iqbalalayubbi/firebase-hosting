<template>
    <button class="bg-primary text-white px-3 py-2 rounded-md" @click="isClick">{{name}}</button>
</template>

<script>
export default {
    name:'Button-Comp',
    props:{
        name:String
    },
    methods:{
        isClick(){
            this.$emit('isClick','')
        }
    }
}
</script>

<style>

</style>