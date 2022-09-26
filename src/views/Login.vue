<template>
    <div class="bg-sky-500 h-screen flex flex-col items-center gap-5">
        <div class="pt-28 flex flex-col w-[80%] gap-2">
            <label for="">usename</label>
            <Input ref="username" class="rounded-md h-8" />
        </div>
        <div class="flex flex-col w-[80%] gap-2">
            <label for="">password</label>
            <Input ref="password" class="rounded-md h-8" />
        </div>
        <Button @isClick="onClick" class=" w-[80%]" name="Login"/>
    </div>
</template>

<script>
import Input from '@/components/Input.vue'
import Button from '@/components/Button.vue'

export default {
    name:'Input-View',
    components : {Input,Button},
    methods:{
        onClick(){
            const ref = this.$refs
            const username = ref.username.$refs.input.value
            const password = ref.password.$refs.input.value

            if (username == 'admin' && password == 'admin'){
                fetch('https://firebase-nodejs-new.herokuapp.com/items').then(res => res.json()).then(result => {
                    localStorage.setItem('items',JSON.stringify(result.data))
                    this.$router.push('/home')
                })
            }
        }
    }
}
</script>

<style>

</style>