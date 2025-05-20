<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';
import Header from '../components/Header.vue';

const trabalhos = ref([]);

const carregarTrabalhos = async () => {
    try {
        const res = await axios.get('https://www.arbeitnow.com/api/job-board-api');
        trabalhos.value = res.data.data;
    } catch (error) {
        console.error('Erro ao carregar os trabalhos:', error);
    } finally {
        console.log("Acabou.");
    }
}

onMounted(() => {
    carregarTrabalhos();
});
</script>

<template>
    <div class="flex flex-col gap-7">
        <Header/>
        <main class="flex flex-col items-center">
            <div class="grid grid-cols-4 w-[80%] gap-5">
                <div v-for="trabalho in trabalhos" :key="trabalho.slug" class="mb-4 p-5 h-50 shadow flex flex-col justify-between">
                    <div class="font-bold">{{ trabalho.title }}</div>
                    <div>{{ trabalho.company_name }}</div>
                    <a :href="trabalho.url" target="_blank" class="text-blue-500">Ver vaga</a>
                </div>
            </div>
        </main>
    </div>

</template>
