<script setup>
import { ref } from 'vue';
import axios from 'axios';
import { useRouter } from 'vue-router';

const username = ref('');
const email = ref('');
const firstName = ref('');
const lastName = ref('');
const gender = ref('');
const age = ref('');
const password = ref('');
const router = useRouter();

const logar = () => {
  axios.post('https://dummyjson.com/users/add', {
    username: username.value,
    email: email.value,
    firstName: firstName.value,
    lastName: lastName.value,
    gender: gender.value,
    age: age.value,
    password: password.value
  }).then((res) => {
    console.log(res)
  }).catch((e) => {
    console.log(e)
  }).finally(() => {
    console.log("Acabou.")
  })
}

const login = () => {
  router.push('/');
}
</script>

<template>
    <main class="flex justify-center items-center w-screen h-screen bg-gray-100">
      <div class="flex flex-col gap-6 p-6 bg-white shadow-lg rounded-lg w-full sm:w-96">
        <h1 class="font-bold text-2xl text-center text-gray-800">CADASTRO</h1>
        <form @submit.prevent="logar" class="flex flex-col gap-3">
  
          <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
            <div class="flex flex-col w-auto">
              <label for="username">Nome de usuário:</label>
              <input type="text" class="border rounded p-2 border-gray-300 focus:outline-none focus:ring-2 focus:ring-blue-500" placeholder="Ex: igorbedon" v-model="username" required/>
            </div>

            <div class="flex flex-col">
              <label for="firstName">Primeiro nome:</label>
              <input type="text" class="border rounded p-2 border-gray-300 focus:outline-none focus:ring-2 focus:ring-blue-500" placeholder="Ex: Igor" v-model="firstName" required/>
            </div>
          </div>

          <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
            <div class="flex flex-col">
              <label for="lastName">Sobrenome</label>
              <input type="text" class="border rounded p-2 border-gray-300 focus:outline-none focus:ring-2 focus:ring-blue-500" placeholder="Ex: Bedon" v-model="lastName" required/>
            </div>
            
            <div class="flex flex-col">
              <label for="password">Senha:</label>
              <input type="password" class="border rounded p-2 border-gray-300 focus:outline-none focus:ring-2 focus:ring-blue-500" placeholder="Ex: amoaisabella" v-model="password" required/>
            </div>
          </div>
  
          <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
            <div class="flex flex-col">
              <label for="gender">Gênero:</label>
              <input type="text" class="border rounded p-2 border-gray-300 focus:outline-none focus:ring-2 focus:ring-blue-500" placeholder="Ex: masculino" v-model="gender" required/>
            </div>
            
            <div class="flex flex-col">
              <label for="age">Idade:</label>
              <input type="number" class="border rounded p-2 border-gray-300 focus:outline-none focus:ring-2 focus:ring-blue-500" placeholder="Ex: 20" v-model="age" required/>
            </div>
          </div>
  
          <div class="grid grid-cols-1 gap-4">
            <div class="flex flex-col">
              <label for="email">email</label>
              <input type="email" class="border rounded p-2 border-gray-300 focus:outline-none focus:ring-2 focus:ring-blue-500" placeholder="Ex: igor@example.com" v-model="email" required/>
            </div>
          </div>
          <button type="submit" class="bg-pink-300 text-white p-3 rounded-md font-semibold hover:bg-pink-400 transition">CADASTRAR</button>
        </form>
        
        <button @click="login" class="border-2 border-pink-300 text-gray-500 p-3 rounded-md font-semibold hover:border-pink-400 transition">LOGAR</button>
      </div>
    </main>
  </template>
