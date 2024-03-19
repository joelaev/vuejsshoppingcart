<script setup>
//importndo una funcion para crear referencias reactivas
import {ref} from 'vue'
//crendo referencia constante activa (conjunto de variables es el "estado de componente")
const header =ref('app lista de compras')
const shoppingIcons =ref('material-icons shopping-cart-icon');
//creando una referencia para
  //almacenar elvalor de una lista
  const items = ref([
   {id: 0, label:'Leche', purchased:false, highPriority: true},
   {id: 1, label:'Arroz', purchased:false, highPriority: false},
   {id: 2, label:'Carne', purchased:true, highPriority: true},
   {id: 3, label:'Pan', purchased:false, highPriority: false},
   {id: 4, label:'huevos', purchased:true, highPriority: true}
  ])
  const newItem =ref('')
  const newItemHighPriority =ref('false')
  //metodos
  const saveItems=()=>{
    //agrega un nuevo item provenuente de la caja de texto
    items.value.push({id: items.value.length, label:newItem.value})
    //borrar contenido de la caja de texto
    newItem.value="";
  }  
  const doEdit=(edit)=>{
    editing.value=edit
    newItem.value="";
  }
  const editing =ref(false)
</script>

<template>
  <!-- Header -->
  <div class="header">
    <h1><i :class="shoppingIcons">local_mall</i> {{ header }}
    </h1>
    <button  v-on:click="doEdit(false)" v-if="editing" 
    class="btn">Cancelar</button>
    <button v-else v-on:click="doEdit(true)"
     class="btn btn-primary">Agregar Articulo</button>
  </div>  

  <form v-if="editing"
  v-on:submit.prevent="saveItems"
   class="add-item form">
  <input v-model="newItem" type="text" placeholder ="agregar articulo">
  <label>
    <input type="checkbox" v-model="newItemHighPriority" >Alta prioridad 
  </label>
  <button class="btn btn-primary">Agregar Articulo</button>
  </form>
  <!-- entrega de lista -->
    <ul>
    <li v-for="{id, label,purchased, highPriority} in items" 
    :class="{priority:highPriority, strikeout:purchased}"
    v-bind:key="id">⭐ {{label}}</li>
  </ul>
  <!-- mensaje condicional -->
  <p v-if="items.length==0">🥀No hay elementos en la lista</p>
</template>
<style scoped>
.shopping-cart-icon{
font-size: 2 rm;
}
</style>