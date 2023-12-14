<script setup>
const props = defineProps(["taskName"]);
</script>

<template>
  <div className="bg-white rounded p-3 space-y-2">
    <p class="text-sm">{{ taskName }}</p>
    <div className="flex flex-row space-x-3">
      <button class="text-blue-500">
        <font-awesome-icon
          icon="fas fa-arrow-left"
          size="xs"
        ></font-awesome-icon>
      </button>
      <button class="text-blue-500">
        <font-awesome-icon
          icon="fas fa-arrow-right"
          size="xs"
        ></font-awesome-icon>
      </button>
      <button class="text-red-500">
        <font-awesome-icon icon="fas fa-times-circle"> </font-awesome-icon>
      </button>
    </div>
  </div>
</template>
