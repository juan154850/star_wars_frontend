<template>
  <Nav />
  <Header />
  <router-view />
  <footer class="text-center py-4 my-4 border-top">
    <p>
      &copy; 2023 by Star Wars APP. Proudly created with Vue.js
    </p>
  </footer>
</template>

<script>
import Nav from './components/Nav.vue';
import Header from './components/Header.vue';
export default {
  components: {
    Nav,
    Header,
  },

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.nav-link:hover {
  text-decoration: underline;
}
</style>
