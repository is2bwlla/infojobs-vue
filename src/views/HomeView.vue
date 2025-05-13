<script setup>
import { ref } from 'vue';
import axios from 'axios';


const username = ref();
const password = ref();

const logar =() => {
  axios.post('https://dummyjson.com/user/login', {
    username: username.value,
    password: password.value
  }).then((res) => {
    console.log(res)
  }).catch((e) => {
    console.log(e)
  }).finally(() => {
    console.log("Acabou.")
  })
}

</script>

<template>
  <main class="flex justify-center items-center w-screen h-screen">
    <div class="flex flex-col gap-2">
      <h1 class="font-bold text-3xl">CREDENCIAIS</h1>
      <input type="text" class="border rounded p-1.5" v-model="username">
      <input type="text" class="border rounded p-1.5" v-model="password">
      <button @click="logar" class="border border-pink-300 bg-pink-300 rounded p-2 text-white font-bold">LOGIN</button>
    </div>
    
  </main>
</template>
