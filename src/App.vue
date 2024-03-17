<script setup>
//Importando funcion para crear referencias reactivas
import { ref } from 'vue'
//Creando una referencia de tipo string
const header = ref('App Lista de compras');
const shoppingIcon = ref('material-icons shopping-cart-icon');
//Creando un referencia reactiva para almacenar el valor de la lista
const items = ref([
  {id: 0, label:'Leche'},
  {id: 1, label:'Arroz'},
  {id: 2, label:'Carne'},
  {id: 3, label:'Pan'},
  {id: 4, label:'Galletas'}
]);
const newItem = ref('');
const newItemHighPriority = ref (false)
</script>

<template>
  <h1> <i v-bind:class="shoppingIcon">local_mall</i> {{ header }}</h1>
  <input v-model="newItem" type="text" placeholder="Agregar Articulo">

 <label><input type="checkbox" v-model="newItemHighPriority">Alta Prioridad</label>
  <div class="add-item form">
    <input v-model="newItem" type="text" placeholder="Agregar Articulo">
    <label><input type="checkbox" v-model="newItemHighPriority">Alta Prioridad</label>
    <button class="btn btn-primary" v-on:click="items.push({ id: items.length, label: newItem})">
    Agrear Articulo</button>
  </div>

  <ul>
    <li v-for="({id, label}, i) in items" v-bind:key="id">⭐{{ label }}</li>
  </ul>
</template>
<style scoped>
.shopping-cart-icon {
  font-size: 2rem;
}
</style>