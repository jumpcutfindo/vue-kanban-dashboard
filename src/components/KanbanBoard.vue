<script setup>
import { ref, reactive } from "vue";
import TaskInput from "./TaskInput.vue";
import TaskList from "./TaskList.vue";

const groups = ref([
  { id: 0, name: "To Do" },
  { id: 1, name: "In Progress" },
  { id: 2, name: "Blocked" },
  { id: 3, name: "Complete" },
]);

const taskLists = ref([
  [{ name: "Buy groceries for the team" }],
  [{ name: "Review Starfield on Steam" }],
  [],
  [{ name: "Cook lunch for dinner" }],
]);

function addTask(name) {
  taskLists.value[0].push({ name });
}

function moveTask(task, from, to) {
  if (to < 0 || to >= taskLists.length) return;

  taskLists.value[from] = taskLists.value[from].filter((t) => t !== task);
  taskLists.value[to].push(task);
}

function removeTask(task, from) {
  taskLists.value[from] = taskLists.value[from].filter((t) => t !== task);
}
</script>

<template>
  <div class="flex flex-col flex-grow space-y-4">
    <div class="flex justify-center">
      <h1 class="text-3xl font-semibold">Vue Kanban Dashboard</h1>
    </div>
    <div class="flex flex-col min-w-full">
      <TaskInput :on-add-task="addTask" />
    </div>
    <div class="flex flex-row flex-grow min-w-full justify-between space-x-4">
      <TaskList
        v-for="(taskList, index) in taskLists"
        v-bind:key="index"
        v-model="taskLists[index]"
        :group-id="index"
        :group-name="groups[index].name"
        :groups-length="taskLists.length"
        :on-move-task="moveTask"
        :on-remove-task="removeTask"
      />
    </div>
  </div>
</template>
