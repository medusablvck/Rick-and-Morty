<script setup>
defineProps({
    character: {
        type: Object,
        required: true
    }
});
</script>

<template>
    <div class="card">
        <img :src="character.image" :alt="character.name">
        <div class="card-info">
            <h3>{{ character.name }}</h3>
            <p>Status: {{ character.status }}</p>
            <p>Species: {{ character.species }}</p>
            <p>Gender: {{ character.gender }}</p>
            <p>Location: {{ character.location.name || 'Unknown' }}</p>
        </div>
    </div>
</template>

<style scoped>
.card {
    border-radius: 8px;
    max-width: 250px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.card-info {
    padding: 15px;
}

img {
    width: 100%;
    cursor: pointer;
    transition: all 0.7s ease;
}

img:hover {
    box-shadow: -3px 6px 24px 3px rgba(35, 78, 38, 0.2);
    transform: scale(1.05);
}
</style>
