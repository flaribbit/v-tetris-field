<template>
  <div>
    <table>
      <tbody>
        <tr v-for="row in field">
          <td v-for="cell in row" :class="['block', cell]"></td>
        </tr>
      </tbody>
    </table>
  </div>
  <div>
    <button v-for="page, i in pages" @click="selectpage = i">{{ i }}</button>
  </div>
</template>

<script setup>
import { ref, computed } from "vue"
import { decoder } from "tetris-fumen"
const props = defineProps({
  fumen: { type: String, default: "v115@vhAAgH" },
})
const pages = ref(decoder.decode(props.fumen));
const selectpage = ref(0)
const field = computed(() => {
  var field = pages.value[selectpage.value].field
  var ret = []
  for (var i = 0; i < 20; i++) {
    var line = []
    for (var j = 0; j < 10; j++) {
      line.push(field.at(j, 19 - i))
    }
    ret.push(line)
  }
  return ret
})
</script>

<style scoped>
.block {
  width: 10px;
  height: 10px;
  border: 1px solid black;
}
.block.T {
  background-color: #f00;
}
.block.I {
  background-color: #00f;
}
.block.O {
  background-color: #0f0;
}
.block.L {
  background-color: #f0f;
}
.block.J {
  background-color: #ff0;
}
.block.S {
  background-color: #0ff;
}
.block.Z {
  background-color: #f0f;
}
</style>
