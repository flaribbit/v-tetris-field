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
