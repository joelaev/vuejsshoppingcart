<script setup>
//importndo una funcion para crear referencias reactivas
import {ref} from 'vue'
//crendo referencia constante activa (conjunto de variables es el "estado de componente")
const header =ref('app lista de compras')
const shoppingIcons =ref('material-icons shopping-cart-icon');
</script>

<template>
  <h1><i :class="shoppingIcons">local_ mall</i> {{ header }}</h1>
</template>

<style scoped>
.shopping-cart-icon{
font-size: 2 rm;
}
</style>
