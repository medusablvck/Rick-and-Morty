<script setup>
defineProps({
    character : {
        type: Object,
        required: true
    }
});
</script>

<template>
    <div class="card">
        <img :src="character.image" :alt="character.name">
        <div class="card-info">
            <h3>{{character.name}}</h3>
            <p>Status: {{character.status}}</p>
            <p>Species: {{character.species}}</p>
            <p>Gender: {{character.gender}}</p>
            <p>Location: {{character.location}}</p>
        </div>
    </div>
</template>

<style scoped>

</style>
