<script setup>
const props = defineProps(["taskName"]);
</script>

<template>
  <div className="bg-white rounded p-3">
    <p class="text-sm">{{ taskName }}</p>
  </div>
</template>
