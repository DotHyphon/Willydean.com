<script setup>
import { createApp } from 'vue';
import { RouterView } from 'vue-router'
import NavBar from './components/NavBar.vue'
</script>

<template>
  <NavBar />

  <RouterView />
</template>

<style scoped>
</style>

<script>
export default {

}
</script>

<!--
  git add *
  git commit -m "'comment'"
  git push origin main
  -->

  <!-- colour pallete
  Red         #e50914
  dark Red    #B1060F
  Heading     #ddd
  text   #686868
  background  #161616
  -->