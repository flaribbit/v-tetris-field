<template>
  <button class="vt-btn" @click="emit('click')">
    <slot />
  </button>
</template>

<script setup lang="ts">
const emit = defineEmits(["click"])
</script>

<style>
button.vt-btn {
  color: white;
  border: none;
  font-size: 16px;
  background-color: #66c65c;
  border-bottom: 4px solid #49b13e;
  padding: 4px 12px;
  margin-right: 8px;
}
button.vt-btn:hover {
  background-color: #78cd6f;
}
button.vt-btn:active {
  background-clip: padding-box;
  border-top: 4px solid transparent;
  border-bottom: none;
}
</style>
