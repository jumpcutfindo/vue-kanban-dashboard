<script setup>
import { ref } from "vue";
import TaskInput from "./TaskInput.vue";
import TaskList from "./TaskList.vue";

const groups = ref([
  { name: "To Do" },
  { name: "In Progress" },
  { name: "Blocked" },
  { name: "Complete" },
]);
</script>

<template>
  <div class="space-y-4">
    <div class="flex justify-center">
      <h1 class="text-3xl font-semibold">Vue Kanban Dashboard</h1>
    </div>
    <div class="flex flex-col min-w-full">
      <TaskInput />
    </div>
    <div class="flex flex-row min-w-full justify-between">
      <div v-for="group in groups">
        <TaskList />
      </div>
    </div>
  </div>
</template>
