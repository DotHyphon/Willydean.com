<script setup>
import { RouterView } from 'vue-router'
import NavBar from './components/NavBar.vue'
</script>

<template>
  <header>
    <NavBar />
  </header>

  <RouterView />
</template>

<style scoped>
</style>

<!--
  git add *
  git commit -m "'comment'"
  git push origin master
  -->
