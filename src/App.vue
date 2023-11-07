<template>
  <nav class="navbar navbar-expand-lg ftco_navbar ftco-navbar-light" id="ftco-navbar">
    <div class="container">
      <router-link to="/" class="navbar-brand">Star Wars APP</router-link>
      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#ftco-nav" aria-controls="ftco-nav"
        aria-expanded="false" aria-label="Toggle navigation">
        <span class="fa fa-bars"></span> Menu
      </button>
      <div class="collapse navbar-collapse" id="ftco-nav">
        <ul class="navbar-nav ml-auto">
          <li class="nav-item">
            <router-link to="/" class="nav-link">Inicio</router-link>
          </li>
          <li class="nav-item">
            <router-link to="/login" class="nav-link">Login</router-link>
          </li>
        </ul>
      </div>
    </div>
  </nav>
  <header class="bg-dark py-3">
    <div class="container">
      <img src="./assets/star-wars-logo.png" alt="Star Wars Logo" class="img-fluid">
    </div>
  </header>
  <router-view />

  <footer class="text-center py-4 my-4 border-top">
    <p>
      &copy; 2023 by Star Wars APP. Proudly created with Vue.js
    </p>

  </footer>
</template>

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
