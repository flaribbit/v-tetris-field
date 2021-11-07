<template>
  <div>{{ field }}</div>
</template>

<script setup>
import { ref } from 'vue'
import { decoder } from 'tetris-fumen'
var data = "v115@vhGRQYHAvItJEJmhCAUGJKJJvMJTNJGBJFKYPAUEzP?EJG98AQmqhECDdCA"
var pages = decoder.decode(data)
const field = ref("")
field.value = pages[0].field.str()
console.log(pages)
</script>
