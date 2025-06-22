<script setup>
import { ref, onMounted, watch } from 'vue';
import axios from 'axios';
import Card from './Card.vue';

const characters = ref([]); //Массив для хранения данных о персонажах, который изначально пустой
const isLoading = ref(true); // Это переменная загрузки
const error = ref(null); // Это переменная хранения ошибки
const totalPages = ref(1);

const props = defineProps({
    filters: {
        type: Object,
        default: () => ({})
    }
});
// Функция, которая отправляет запрос к апи, после чего сохраняет результат в переменную о персонажах, если возникает ошибка, она сохраняется в переменную error
const fetchCharacters = async (filters = {}) => {
    try {
        isLoading.value = true;
        const params = {
            ...filters,
            page: 1 // Можно добавить пагинацию
        };

        const response = await axios.get('https://rickandmortyapi.com/api/character', { params });
        characters.value = response.data.results;
        totalPages.value = response.data.info.pages;
    } catch (err) {
        error.value = 'Failed to fetch characters';
        console.log(err);
    } finally {
        isLoading.value = false;
    };
    // try {
    //     const response = await axios.get('https://rickandmortyapi.com/api/character');
    //     characters.value = response.data.results;
    // } catch (err) {
    //     error.value = 'Failed to fetch characters';
    //     console.log(err);
    // } finally {
    //     isLoading.value = false;
    // };
}

//хук запускает фунцию fetchCharacters
onMounted(() => {
    fetchCharacters();
});
watch(() => props.filters, (newFilters) => {
    fetchCharacters(newFilters);
}, { deep: true });
</script>

<template>
    <section>
        <h1>Come on, in and out, 20-minute adventure!</h1>
        <p>Click on any character or use the search bar!</p>

        <div v-if="isLoading"> Loading characters </div>
        <div v-else-if="error"> {{ error }} </div>
        <div v-else class="character-grid">
            <Card v-for="character in characters" :key="character.id" :character="character" />
        </div>
    </section>

</template>

<style scoped>
h1 {
    text-align: center;
    padding: 2rem;
    font-size: 2.5rem;
}

p {
    text-align: center;
    font-size: 1.3rem;
}

.character-grid {
    display: grid;
    justify-items: center;
    grid-template-columns: repeat(5, 1fr);
    padding: 2rem;
    gap: 1.2rem;
}

.error {
    color: red;
    text-align: center;
}
@media (max-width:900px){
    .character-grid{
        grid-template-columns: repeat(4,1fr);
    }
}
@media (max-width:600px){
    .character-grid{
        grid-template-columns: repeat(3,1fr);
    }
    h1{
        font-size: 2.2rem;
    }
}
@media (max-width:400px){
    .character-grid{
        grid-template-columns: repeat(2,1fr);
    }
}

</style>
