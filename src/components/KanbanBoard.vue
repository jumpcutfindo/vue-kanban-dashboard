<script setup>
import { ref } from "vue";
import TaskInput from "./TaskInput.vue";
import TaskList from "./TaskList.vue";

const tasks = ref([
  { groupId: 0, name: "Buy groceries for the team" },
  { groupId: 1, name: "Review Starfield on Steam" },
]);

const groups = ref([
  { id: 0, name: "To Do" },
  { id: 1, name: "In Progress" },
  { id: 2, name: "Blocked" },
  { id: 3, name: "Complete" },
]);
</script>

<template>
  <div class="flex flex-col flex-grow space-y-4">
    <div class="flex justify-center">
      <h1 class="text-3xl font-semibold">Vue Kanban Dashboard</h1>
    </div>
    <div class="flex flex-col min-w-full">
      <TaskInput />
    </div>
    <div class="flex flex-row flex-grow min-w-full justify-between space-x-4">
      <TaskList
        v-for="group in groups"
        :group-name="group.name"
        :tasks="tasks.filter((t) => t.groupId === group.id)"
      />
    </div>
  </div>
</template>
