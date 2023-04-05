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
    <ScrollingRow :displayText="'MyProjects'" :links="myLinks"/>
    <ScrollingRow :displayText="titles[Math.floor(Math.random()*titles.length)]" placeHolder/>
    <ScrollingRow :displayText="titles[Math.floor(Math.random()*titles.length)]" placeHolder/>
    <ScrollingRow :displayText="titles[Math.floor(Math.random()*titles.length)]" placeHolder/>
    <ScrollingRow :displayText="titles[Math.floor(Math.random()*titles.length)]" placeHolder/>
    <ScrollingRow :displayText="titles[Math.floor(Math.random()*titles.length)]" placeHolder/>
    <ScrollingRow :displayText="titles[Math.floor(Math.random()*titles.length)]" placeHolder/>
    <ScrollingRow :displayText="titles[Math.floor(Math.random()*titles.length)]" placeHolder/>
    <ScrollingRow :displayText="titles[Math.floor(Math.random()*titles.length)]" placeHolder/>
    <ScrollingRow :displayText="titles[Math.floor(Math.random()*titles.length)]" placeHolder/>
    <ScrollingRow :displayText="titles[Math.floor(Math.random()*titles.length)]" placeHolder/>
    <ScrollingRow :displayText="titles[Math.floor(Math.random()*titles.length)]" placeHolder/>
    <ScrollingRow :displayText="titles[Math.floor(Math.random()*titles.length)]" placeHolder/>
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
      ],
      myLinks: [
        {
          title: "Photo Demo",
          url: "https://willydean.com/photodemo",
          image: "https://willydean.com/photodemo/preview.png",
          blank: false,
        },
        {
          title: "Snake Game",
          url: "https://willydean.com/snakegame",
          image: "https://willydean.com/snakegame/preview.png",
          blank: false,
        },
      ]
    }
  },
}


</script>

<style scoped>
</style>