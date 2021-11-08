<template>
  <button @click="emit('click')">
    <slot />
  </button>
</template>

<script setup>
const emit = defineEmits(["click"])
</script>

<style scoped>
button {
  color: white;
  border: none;
  font-size: 16px;
  background-color: #66c65c;
  border-bottom: 4px solid #49b13e;
  padding: 4px 12px;
  margin-right: 8px;
}
button:hover {
  background-color: #78cd6f;
}
button:active {
  background-clip: padding-box;
  border-top: 4px solid transparent;
  border-bottom: none;
}
</style>
