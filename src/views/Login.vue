<script setup>
import { ref } from 'vue';
import axios from 'axios';
import { useRouter } from 'vue-router';

const username = ref('');
const password = ref('');

const router = useRouter();

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
    router.push('/home')
  })
}

const cadastrar = () => {
  router.push('/signup');
}

</script>

<template>
  <main class="flex justify-center items-center w-screen h-screen">
    <div class="flex flex-col gap-2 items-center">
      <h1 class="font-bold text-2xl">LOGIN</h1>
      <input type="text" class="border rounded p-1.5 border-gray-500" placeholder="Ex: Igor Bedon" v-model="username">
      <input type="password" class="border rounded p-1.5 border-gray-500" placeholder="password" v-model="password">
      <button @click="logar" class="border border-pink-300 bg-pink-300 rounded p-2 text-white font-bold w-full">LOGIN</button>
      <button @click="cadastrar" class="border-pink-300 border-2 rounded font-bold p-2 text-gray-500 w-full">CADASTRAR</button>
    </div>
  </main>
</template>
