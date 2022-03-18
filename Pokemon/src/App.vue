<script setup>
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import HelloWorld from './components/HelloWorld.vue'
import PictureCarousel from './components/PictureCarousel.vue';
import TopNavBar from './components/TopNavBar.vue';
import Header from './components/Header.vue';
</script>

<template>
  <TopNavBar />
  <Header />
  <PictureCarousel />

</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
