<script setup>
//importndo una funcion para crear referencias reactivas
  import { ref } from 'vue';
//crendo referencia constante activa (conjunto de variables es el "estado de componente")
  const header = ref('app lista de compras');
  const shoppingIcons = ref('material-icons shopping-cart-icon');
//creando una referencia para
  //almacenar elvalor de una lista
  const items = ref([
   //{id: 0, label:'Leche'},
   //{id: 1, label:'Arroz'},
   //{id: 2, label:'Carne'},
   //{id: 3, label:'Pan'},
   //{id: 4, label:'huevos'}
  ]);
  const newItem = ref('');
  const newItemHighPriority = ref(false);
  const add = ref(true);
  //metodos
  const saveItems = () => {
    items.value.push({ id: items.value.length, label: newItem.value });
    newItem.value = '';
  };

  const toggleForm = () => {
    add.value = !add.value;
  };
</script>
<template>
  <!-- Header -->
  <div class="header">
    <h1><i :class="shoppingIcons">local_mall</i> {{ header }}</h1>
      <!-- Botón "Agregar Articulo" -->
    <p v-show="add">
      <button class="btn btn-primary" @click="toggleForm">Agregar Articulo</button>
    </p>
     <!-- Botón "Cancelar" -->
    <p v-show="!add">
      <button class="btn" @click="toggleForm">Cancelar</button>
    </p>
  </div> 
  <!-- Formulario -->
  <form v-show="!add" v-on:submit.prevent="saveItems" class="add-item form">
    <input v-model="newItem" type="text" placeholder="Agregar artículo">
    <label>
      <input type="checkbox" v-model="newItemHighPriority">Alta prioridad 
    </label>
    <button class="btn btn-primary">Agregar Articulo</button>
  </form>

  <!-- Lista de items -->
  <ul>
    <li v-for="{id, label} in items" v-bind:key="id">⭐ {{label}}</li>
  </ul>

  <!-- Mensaje condicional -->
  <p v-if="items.length === 0">🥀 No hay elementos en la lista</p>
</template>



<style scoped>
  .shopping-cart-icon {
    font-size: 2rem;
  }
</style>
