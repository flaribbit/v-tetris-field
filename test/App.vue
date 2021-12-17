<template>
  <h2>TFumenPlayer</h2>
  <TFumenPlayer :fumen="fumen" :page="0" />
  <h2>TFumenList</h2>
  <TFumenList :fumen="fumen" :height="10" />
</template>

<script setup lang="ts">
import TFumenPlayer from '../src/TFumenPlayer.vue';
import TFumenList from '../src/TFumenList.vue';
var fumen = "v115@vhPJHYaAkeEfEXoC+BlvlzByEEfE03k2AlP5ABwfAA?A+rQAAqsBsqBvtBTpBVhQeAlvlzByEEfE03k2AlP5ABwvDf?E33ZBBlfbOBV5AAAOfQeAlvlzByEEfE03+2BlP5ABwvDfEV?5k2AlPJVBjzAAA6WQAAzdBpeB0XBXUBFlQnAlvlzByEEfE0?3+2BlP5ABwvDfEXhWEBUYPNBkkuRA1GCLBUupAAdqQnAlvl?zByEEfE038UBlP5ABwvDfEXhWEBUYPNBkkuRA1GCLBU+rAA?AAPAA"
if (location.search.length > 0) fumen = location.search.substring(1);
</script>

<style>
.vt-field {
  background-color: #f3f3ed;
  border-radius: 4px;
}
@media (max-width: 420px) {
  .fumen-item {
    width: calc(50% - 4px);
  }
  .fumen-item .vt-field {
    width: 100%;
  }
}
</style>
