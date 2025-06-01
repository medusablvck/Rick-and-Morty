<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';
import Card from './Card.vue';

const characters = ref([]); //Массив для хранения данных о персонажах, который изначально пустой
const isLoading = ref(true); // Переменная загрузки
const error = ref(null); // Переменная хранения ошибки


// Функция, которая отправляет запрос к апи, после чего сохраняет результат в переменную о персонажах, если возникает ошибка, она сохраняется в переменную error
const fetchCharacters = async() => {
    try{
        const response = await axios.get('https://rickandmortyapi.com/api/character');
        characters.value = response.data.results;
    } catch(err) {
        error.value = 'Failed to fetch characters';
        console.log(err);
    } finally{
        isLoading.value = false;
    };
} 

//хук запускает фунцию fetchCharacters
onMounted(() =>{
    fetchCharacters();
})
</script>

<template>
    <section>
        <h1>Come on, in and out, 20-minute adventure!</h1>
        <p>Click on any character or use the search bar!</p>
    </section>

</template>

<style scoped>

h1{
    text-align: center;
    padding: 2rem;
    font-size: 2.5rem;
}
p{
    text-align: center;
    font-size: 1.3rem;
}
</style>
