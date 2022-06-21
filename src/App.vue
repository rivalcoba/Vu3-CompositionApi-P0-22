<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import { ref } from "vue";
// Variable que controla la visualizacuib el formulario
const editing = ref(false);
const header = ref("🛒 Shopping List App");
const items = ref([
  // { id: 1, label: "10 bolillos" },
  // { id: 2, label: "1 lata de frijoles" },
  // { id: 3, label: "2 lata de atún" },
]);
const newItem = ref("");
const newItemHighPriority = ref(false);
// Metodo para agregar nuevos elementos a la lista
const saveItem = () => {
  items.value.push({ id: items.value.length + 1, label: newItem.value });
  // Reiniciendo la entrada de texto
  newItem.value = "";
};
// Funcion que alterna el valor de la variable editing
const doEdit = (edit)=>{
  editing.value = edit;
  // Limpiando la entrada de texto
  // en caso de que se oculte o muestre
  // el formulario
  newItem.value = "";
};
</script>

<template>
  <div class="header">
    <h1>{{ header }}</h1>
    <button v-if="editing" @click="doEdit(false)" class="btn">Cancel</button>
    <button v-else @click="doEdit(true)" class="btn btn-primary">Add Item</button>
  </div>

  <!-- Agrupando en un div las entradas -->
  <form v-if="editing" v-on:submit.prevent="saveItem" class="add-item form">
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
  <p v-if="items.length === 0">🥀 No hay elementos en la lista</p>
</template>
