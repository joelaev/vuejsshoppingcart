<template>
  <!-- Header -->
  <div class="header">
    <h1><i :class="shoppingIcons">local_mall</i> {{ header }}</h1>
    
    <p v-show="add">
      <button class="btn btn-primary" @click="toggleForm">Agregar Articulo</button>
    </p>
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

<script setup>
  import { ref } from 'vue';

  const header = ref('app lista de compras');
  const shoppingIcons = ref('material-icons shopping-cart-icon');
  const items = ref([]);
  const newItem = ref('');
  const newItemHighPriority = ref(false);
  const add = ref(true);

  const saveItems = () => {
    items.value.push({ id: items.value.length, label: newItem.value });
    newItem.value = '';
  };

  const toggleForm = () => {
    add.value = !add.value;
  };
</script>

<style scoped>
  .shopping-cart-icon {
    font-size: 2rem;
  }
</style>

