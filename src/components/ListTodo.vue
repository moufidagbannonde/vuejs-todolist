<script setup>
import { defineProps } from 'vue';
 const props = defineProps({
    todos: {
        type: Array,
        required: true
        }
})
const emit = defineEmits(["sendOldTodo"])
const updateTodo = (element, index) => {
    element.id = index
  emit('sendOldTodo', element);
}

// console.log(props.todos);
</script>

<template>
  <ul>
        <li v-for="(todo, index) in todos" :key="index" @dblclick="updateTodo(todo)">{{ todo.titre }}</li>
  </ul>
 </template>



<style scoped>


</style>