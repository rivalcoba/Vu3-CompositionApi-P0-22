<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import { ref } from "vue";

const header = ref("🛒 Shopping List App");
const items = ref([
  { id: 1, label: "10 bolillos" },
  { id: 2, label: "1 lata de frijoles" },
  { id: 3, label: "2 lata de atún" },
]);
const newItem = ref("");
const newItemHighPriority = ref(false);
const iceCreamFlavors = ref([]);
</script>

<template>
  <h1>{{ header }}</h1>
  <input v-model.trim="newItem" type="text" placeholder="Add Item" />
  <!-- Caja de seleccion de prioridad -->
  <label>
    <input type="checkbox" v-model="newItemHighPriority">
    High Priority
  </label>
  <!-- Helados -->
  <label><input type="checkbox" v-model="iceCreamFlavors" value="vanilla">Vanilla</label>
  <label><input type="checkbox" v-model="iceCreamFlavors" value="chocolate">Chocolate</label>
  <label><input type="checkbox" v-model="iceCreamFlavors" value="strawnerry">Strawberry</label>
  {{iceCreamFlavors}}
  <!-- Lista -->
  <ul>
    <li v-for="({ id, label }, index) in items" key="id">⚜ {{ label }}</li>
  </ul>
</template>
