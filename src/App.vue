<script setup>
  import { ref } from 'vue'
  import Chance from 'chance'
  import Item from './components/Item.vue'

  const chance = new Chance()

  const items = ref([])

  setInterval(() => {
    items.value.push({ text: chance.word(), time: Date.now() })
  }, 35)

  setInterval(() => {
    items.value = items.value.filter((item) => item.time > Date.now() - 1000)
  }, 1000)
</script>

<template>
  <div v-for="item in items">{{ item.text }}</div>
  <!-- <Item v-for="item in items">{{ item.text }}</Item> -->
</template>
