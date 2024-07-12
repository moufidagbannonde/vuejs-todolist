<script setup>

import { ref } from 'vue'

import Formulaire from './components/Formulaire.vue';
import ListTodo from './components/ListTodo.vue';

const todos = ref([
  {titre:"Finir mon exo js", statut:"En cours", categorie:"Cours"},
  {titre:"Finir mon exo Vue", statut:"Terminé", categorie:"Cours"},
  {titre:"Faire du body attack", statut:"En cours", categorie:"Sport"},
]);
const oldTodoTitle = ref('test')

const addList = (param) => {
  todos.value.push({titre:param, statut: "En cours", categorie: "Cours"})
  // console.log(param);
}
const takeOldTodo = (event) => {
    oldTodoTitle.value = event.titre;
    console.log(event.titre);
}
const editData = ()=>{
  
}

</script>

<template>
<h1>Bienvenu(e) dans l'univers des tâches</h1><br>

 <Formulaire @request="addList" :oldTodoProps="oldTodoTitle" @editEvent = "editData"></Formulaire><br>

 <ListTodo :todos = "todos" @sendOldTodo="takeOldTodo"></ListTodo>

</template>



<style>

</style>
