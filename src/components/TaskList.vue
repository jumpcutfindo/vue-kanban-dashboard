<script setup>
import Task from "./Task.vue";

const props = defineProps([
  "modelValue",
  "groupId",
  "groupName",
  "groupsLength",
  "onMoveTask",
]);
const emits = defineEmits(["update:modelValue"]);

function onMoveTaskLeft(task) {
  props.onMoveTask(task, props.groupId, props.groupId - 1);
}

function onMoveTaskRight(task) {
  props.onMoveTask(task, props.groupId, props.groupId + 1);
}
</script>

<template>
  <div class="flex flex-col w-full space-y-2">
    <h2 class="font-xl">{{ groupName }}</h2>
    <div class="flex-grow bg-gray-200 rounded p-2 space-y-2">
      <Task
        v-bind:key="task.name"
        v-for="(task, index) of modelValue"
        v-model="modelValue[index]"
        :group-id="groupId"
        :groups-length="groupsLength"
        :onMoveLeft="onMoveTaskLeft"
        :onMoveRight="onMoveTaskRight"
      ></Task>
    </div>
  </div>
</template>
