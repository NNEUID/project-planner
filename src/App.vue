<!-- eslint-disable -->
<template>
  <Navbar />
  <router-view />
</template>
<script>
/* eslint-disable */
import Navbar from './components/Navbar.vue';
export default {
  components: {
    Navbar
  }
}
</script>
<style>
/* eslint-disable */
body {
  background: #f2f2f2;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #555;
  max-width: 600px;
  margin: 0 auto;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
