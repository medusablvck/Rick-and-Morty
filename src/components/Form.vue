<script setup>
import { ref } from 'vue';

const searchQuery = ref('');
const status = ref('All');
const gender = ref('All');
const emit = defineEmits(['search']);

const handleSearch = () => {
    emit('search', {
        name: searchQuery.value,
        status: status.value === 'All' ? '' : status.value,
        gender: gender.value === 'All' ? '' : gender.value
    });
}
</script>
<template>
    <div class="container">
        <form @submit.prevent="handleSearch" class="form">
            <label for="status">Status:</label>
            <select id="status" v-model="status">
                <option value="All">All</option>
                <option value="Alive">Alive</option>
                <option value="Dead">Dead</option>
                <option value="Unknown">Unknown</option>
            </select>
            <label for="gender">Gender:</label>
            <select id="gender" v-model="gender">
                <option value="All">All</option>
                <option value="Male">Male</option>
                <option value="Female">Female</option>
                <option value="Genderless">Genderless</option>
                <option value="Unknown">Unknown</option>
            </select>
            <input class="search-btn" type="search" v-model="searchQuery" placeholder="search for a character">
        </form>
        <button @click="handleSearch">Search</button>
    </div>

</template>


<style scoped>
.container{
    display: flex;
    position: relative;
    flex-direction: column;
    align-items: center;
}
form {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 10px;
    padding: 2rem;
    border-radius: 9px;
}

select,
input {
    border-radius: 8px;
    padding: 5px;
    border: 1px solid rgb(9, 71, 9);
    font-size: 1rem;
}
label{
    font-size: 1.2rem;
}

button {
    padding: 10px 25px;
    border-radius: 8px;
    border: 1px solid rgb(9, 71, 9);
    background-color: rgba(184, 221, 35, 0.6);
    cursor: pointer;
    font-size: 1rem;
}
</style>
