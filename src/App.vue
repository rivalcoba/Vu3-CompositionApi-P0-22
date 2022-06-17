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
</script>

<template>
  <h1>{{ header }}</h1>

  <!-- Agrupando en un div las entradas -->
  <div class="add-item fomr">
    <!-- entrada de texto -->
    <input
      v-on:keyup.enter="items.push({ id: items.length + 1, label: newItem })"
      v-model.trim="newItem"
      type="text"
      placeholder="Add Item"
    />
    <!-- Caja de seleccion de prioridad -->
    <label>
      <input type="checkbox" v-model="newItemHighPriority" />
      High Priority
    </label>
    <!-- Boton -->
    <button
      v-on:click="items.push({ id: items.length + 1, label: newItem })"
      class="btn btn-primary"
    >
      Save Item
    </button>
  </div>

  <!-- Lista -->
  <ul>
    <li v-for="({ id, label }, index) in items" key="id">⚜ {{ label }}</li>
  </ul>
</template>
