<template>
    <div class="flex flex-col items-center">
      <h1 class="font-bold text-4xl mt-3">List nama siswa</h1>
      <div class="w-[50%] mt-10">
        <table class="text-center text-white w-full">
          <thead class="bg-green-500">
            <th>No</th>
            <th>Nama</th>
            <th>Umur</th>
          </thead>
          <tbody>
            <tr v-for="(user,i) in users" :key="i" class="bg-gray-500">
              <td>{{i+1}}</td>
              <td>{{user.nama}}</td>
              <td>{{user.umur}}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
</template>

<script>
export default {
  name: 'App',
  data(){
    return{
      users:[]
    }
  },
  created(){
    fetch('https://firebase-nodejs-new.herokuapp.com/').then(res => res.json()).then(result => this.users = result)
  }
}
</script>
