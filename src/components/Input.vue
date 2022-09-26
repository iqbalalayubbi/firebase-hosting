<template>
  <input ref="input" @input="isInput" :value="input" type="text" :placeholder="placeholder" class="focus:outline-none indent-3">
</template>

<script>
export default {
    name:'Input-Comp',
    props:{
        placeholder:String,
        input:String
    },
    methods:{
        isInput(){
            this.$emit('isInput',this.$refs.input.value.toLowerCase())
        }
    }
}
</script>

<style>

</style>