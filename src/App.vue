<script setup>
import { ref } from 'vue';
import Header from './components/Header.vue';
import Main from './components/Main.vue';
import Form from './components/Form.vue';
import Footer from './components/Footer.vue';

const filters = ref({});

const handleSearch = (newFilters) => {
  filters.value = newFilters  
  try {
    filters.value = newFilters || {}; // Защита от null/undefined
  } catch (err) {
    console.error('Filter error:', err);
  }
}
</script>

<template>
  <Header  />
  <Form @search="handleSearch" />
  <Main :filters="filters" />
  <Footer />
</template>

<style scoped>

</style>
