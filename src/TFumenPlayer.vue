<template>
  <div>
    <VTetrisField :page="pages[page]" :height="props.height" />
  </div>
  <div class="fumen-ctl">
    <TButton @click="setPage(page - 1)">上一页</TButton>
    <TButton @click="setPage(page + 1)">下一页</TButton>
    {{ page + 1 }}
  </div>
</template>

<script setup>
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
const setPage = (p) => {
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
