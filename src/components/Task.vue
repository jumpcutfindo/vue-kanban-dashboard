<script setup>
const props = defineProps([
  "modelValue",
  "groupId",
  "groupsLength",
  "onMoveLeft",
  "onMoveRight",
  "onRemove",
]);
const emits = defineEmits(["update:modelValue", "onMoveLeft", "onMoveRight"]);
</script>

<template>
  <div class="bg-white rounded p-3 space-y-2">
    <p class="text-sm">{{ modelValue.name }}</p>
    <div class="flex flex-row">
      <div class="flex flex-row space-x-4">
        <button
          class="text-gray-400 disabled:text-gray-300 hover:text-green-500"
          :disabled="groupId <= 0"
          @click="onMoveLeft(modelValue)"
        >
          <font-awesome-icon
            icon="fas fa-arrow-left"
            size="xs"
          ></font-awesome-icon>
        </button>
        <button
          class="text-gray-400 disabled:text-gray-300 hover:text-green-500"
          :disabled="groupId >= groupsLength - 1"
          @click="onMoveRight(modelValue)"
        >
          <font-awesome-icon
            icon="fas fa-arrow-right"
            size="xs"
          ></font-awesome-icon>
        </button>
      </div>
      <div class="flex flex-grow justify-end">
        <button
          class="text-gray-400 disabled:text-gray-300 hover:text-red-500"
          @click="onRemove(modelValue)"
        >
          <font-awesome-icon icon="fas fa-times-circle"></font-awesome-icon>
        </button>
      </div>
    </div>
  </div>
</template>
