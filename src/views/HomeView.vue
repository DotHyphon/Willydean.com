<script setup>
import { createDOMCompilerError } from '@vue/compiler-dom';
import ScrollingRow from '../components/ScrollingRow.vue';
</script>

<template>
  <main>
    <br>
    <br>
    <br>
    <br>
    <ScrollingRow :displayText="titles[Math.floor(Math.random()*titles.length)]"/>
    <ScrollingRow :displayText="titles[Math.floor(Math.random()*titles.length)]"/>
    <ScrollingRow :displayText="titles[Math.floor(Math.random()*titles.length)]"/>
    <ScrollingRow :displayText="titles[Math.floor(Math.random()*titles.length)]"/>
    <ScrollingRow :displayText="titles[Math.floor(Math.random()*titles.length)]"/>
    <ScrollingRow :displayText="titles[Math.floor(Math.random()*titles.length)]"/>
    <ScrollingRow :displayText="titles[Math.floor(Math.random()*titles.length)]"/>
    <ScrollingRow :displayText="titles[Math.floor(Math.random()*titles.length)]"/>
    <ScrollingRow :displayText="titles[Math.floor(Math.random()*titles.length)]"/>
    <ScrollingRow :displayText="titles[Math.floor(Math.random()*titles.length)]"/>
    <ScrollingRow :displayText="titles[Math.floor(Math.random()*titles.length)]"/>
    <ScrollingRow :displayText="titles[Math.floor(Math.random()*titles.length)]"/>
  </main>
</template>

<script>
export default {
  components: {
    ScrollingRow
  },
  data() {
    return {
      titles: [
        "Suggested for you",
        "Popular now",
        "Trending",
        "Newly Added",
        "Must see",
        "The cake is a lie"
      ]
    }
  },
}


</script>

<style scoped>
</style>