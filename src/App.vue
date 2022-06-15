<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import { ref } from 'vue';

const header = ref('🛒 Shopping List App');
const items = ref([
  { id: 1, label: '10 bolillos' },
  { id: 2, label: '1 lata de frijoles' },
  { id: 3, label: '2 lata de atún' },
]);
const newItem = ref('');
</script>

<template>
  <h1>{{ header }}</h1>
  <input v-model.trim="newItem" type="text" placeholder="Add Item" />
  {{ newItem }}
  <ul>
    <li v-for="({ id, label }, index) in items" key="id">⚜ {{ label }}</li>
  </ul>
</template>
