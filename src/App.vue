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
// Metodo para agregar nuevos elementos a la lista
const saveItem = () => {
  items.value.push({ id: items.value.length + 1, label: newItem.value });
  // Reiniciendo la entrada de texto
  newItem.value = "";
};
</script>

<template>
  <h1>{{ header }}</h1>

  <!-- Agrupando en un div las entradas -->
  <form v-on:submit.prevent="saveItem" class="add-item form">
    <!-- entrada de texto -->
    <input v-model.trim="newItem" type="text" placeholder="Add Item" />
    <!-- Caja de seleccion de prioridad -->
    <label>
      <input type="checkbox" v-model="newItemHighPriority" />
      High Priority
    </label>
    <!-- Boton -->
    <button class="btn btn-primary">Save Item</button>
  </form>

  <!-- Lista -->
  <ul>
    <li v-for="{ id, label } in items" v-bind:key="id">⚜ {{ label }}</li>
  </ul>
</template>
