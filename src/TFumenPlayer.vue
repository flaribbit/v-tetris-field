<template>
  <div>
    <VTetrisField :page="pages[page]" :height="props.height" />
  </div>
  <div class="fumen-ctl">
    <TButton @click="setPage(0)">|&lt;</TButton>
    <TButton @click="setPage(page - 1)">&lt;</TButton>
    <TButton @click="setPage(page + 1)">&gt;</TButton>
    <TButton @click="setPage(pages.length - 1)">&gt;|</TButton>
    {{ page + 1 }}
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue"
import { decoder } from "tetris-fumen"
import TButton from "./TButton.vue"
import VTetrisField from "./VTetrisField.vue"
const props = defineProps({
  fumen: { type: String, default: "v115@vhAAgH" },
  page: { type: Number, default: 0 },
  height: { type: Number, default: 20 },
})
const pages = ref(decoder.decode(props.fumen))
const page = ref(props.page)
const setPage = (p: number) => {
  if (p < 0 || p >= pages.value.length) return
  page.value = p
}
</script>

<style>
.fumen-ctl {
  display: flex;
  align-items: center;
}
</style>
