<template>
  <div>
    <canvas ref="canvas" />
  </div>
  <div>
    <button v-for="_, i in pages" @click="page = i">{{ i }}</button>
  </div>
</template>

<script setup>
import { ref, watch, onMounted } from "vue"
import { decoder } from "tetris-fumen"
// color constants
const colors = {
  "T": ["#b451ac", "#e56add"],
  "I": ["#41afde", "#43d3ff"],
  "O": ["#f7d33e", "#fff952"],
  "L": ["#ef9535", "#ffbf60"],
  "J": ["#1983bf", "#1ba6f9"],
  "S": ["#66c65c", "#88ee86"],
  "Z": ["#ef624d", "#ff9484"],
}
const props = defineProps({
  fumen: { type: String, default: "v115@vhAAgH" },
  page: { type: Number, default: 0 },
})
// variables
var ctx = null
const canvas = ref(null)
const pages = ref(decoder.decode(props.fumen));
const page = ref(props.page);
// draw game field
const drawField = () => {
  const field = pages.value[page.value].field
  for (var i = 0; i < 20; i++) {
    for (var j = 0; j < 10; j++) {
      var piece = field.at(j, i)
      if (piece != "_") {
        ctx.fillStyle = colors[piece][0]
        ctx.fillRect(j * 20, (19 - i) * 20, 20, 20)
        ctx.fillStyle = colors[piece][1]
        ctx.fillRect(j * 20, (19 - i) * 20, 20, -4)
      }
    }
  }
}
onMounted(() => {
  canvas.value.width = 10 * 20
  canvas.value.height = 20 * 20
  canvas.value.style = "image-rendering: pixelated"
  ctx = canvas.value.getContext("2d")
  drawField()
})
watch(page, () => {
  ctx.clearRect(0, 0, ctx.canvas.width, ctx.canvas.height)
  drawField()
})
</script>
