<script setup>
import Task from "./Task.vue";

defineProps(["groupName", "tasks"]);
</script>

<template>
  <div class="flex flex-col w-full space-y-2">
    <h2 class="font-xl">{{ groupName }}</h2>
    <div class="flex-grow bg-gray-200 rounded p-2 space-y-2">
      <Task
        v-bind:key="task.name"
        v-for="task of tasks"
        :taskName="task.name"
      ></Task>
    </div>
  </div>
</template>
