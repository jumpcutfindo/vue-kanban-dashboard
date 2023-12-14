<script setup>
import { ref } from "vue";
const { onAddTask } = defineProps(["onAddTask"]);

let taskInput = ref("");

function submitForm(event) {
  event.preventDefault();

  if (taskInput.value === "") return;

  onAddTask(taskInput.value);
  taskInput.value = "";
}
</script>
<template>
  <form class="flex flex-row justify-center space-x-4" @submit="submitForm">
    <input
      v-model="taskInput"
      class="flex-grow max-w-[30%] rounded bg-gray-200 focus:outline-none px-2 py-1"
    />
    <button
      type="submit"
      class="bg-blue-500 text-white py-1 px-2 rounded focus:outline-none"
    >
      Add Task
    </button>
  </form>
</template>
