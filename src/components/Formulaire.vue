<script setup>
import { onUpdated, ref } from "vue";
const showBtn = ref(true);
const emit = defineEmits(["request", "editEvent"]);
const props = defineProps({
  oldTodoProps: String,
  required: true,
});
const task = ref("");
const addTodo = (el) => {
  emit("request", el);
};

watch(
  () => props.oldTodoProps,
  (newValue, oldValue) => {
    task.value = newValue;
    showBtn.value = false;
  }
);
const editTodo = () => {
  emit("editEvent", task.value);
};
</script>

<template>
  <div>
    <input
      type="text"
      required
      placeholder="Veuillez ajouter une tâche"
      v-model="task"
    /><br />
    <button v-if="showBtn" @click="addTodo(task)">Ajouter</button>
    <button v-else @click="editTodo">Editer</button>
  </div>
</template>

<style scoped>
</style>