<script setup>
//importndo una funcion para crear referencias reactivas
import {ref} from 'vue'
//crendo referencia constante activa (conjunto de variables es el "estado de componente")
const header =ref('app lista de compras')
const shoppingIcons =ref('material-icons shopping-cart-icon');
//creando una referencia para
  //almacenar elvalor de una lista
  const items = ref([
    {id: 1, label:'Leche'},
   { id: 1, label:'Arroz'}
    {id: 1, label:'Carne'},
   {id: 1, label:'Pan'},
   {id: 1, label:'huevos'}
  ])
</script>

<template>
  <h1><i :class="shoppingIcons">local_ mall</i> {{ header }}</h1>
  <ul>
    <li v-for="item in items" divvi b-bind: key="item">⭐ {(item.label)}</li>
  </ul>
</template>

<style scoped>
.shopping-cart-icon{
font-size: 2 rm;
}
</style>
