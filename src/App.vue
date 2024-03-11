<script setup>
//importndo una funcion para crear referencias reactivas
import {ref} from 'vue'
//crendo referencia constante activa (conjunto de variables es el "estado de componente")
const header =ref('app lista de compras')
const shoppingIcons =ref('material-icons shopping-cart-icon');
//creando una referencia para
  //almacenar elvalor de una lista
  const items = ref([
   {id: 0, label:'Leche'},
   {id: 1, label:'Arroz'},
   {id: 2, label:'Carne'},
   {id: 3, label:'Pan'},
   {id: 4, label:'huevos'}
  ])
</script>

<template>
  <h1><i :class="shoppingIcons">local_mall</i> {{ header }}</h1>
  <ul>
    <li v-for="item in items" v-bind:key="item.id">⭐ {{item.label}}</li>
  </ul>
</template>

<style scoped>
.shopping-cart-icon{
font-size: 2 rm;
}
</style>