<template>
    <nav class="navbar navbar-expand-lg ftco_navbar ftco-navbar-light" id="ftco-navbar">
        <div class="container">
            <router-link to="/" class="navbar-brand">Star Wars APP</router-link>
            <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#ftco-nav"
                aria-controls="ftco-nav" aria-expanded="false" aria-label="Toggle navigation">
                <span class="fa fa-bars"></span> Menu
            </button>
            <div class="collapse navbar-collapse" id="ftco-nav">
                <ul class="navbar-nav ml-auto">
                    <li class="nav-item">
                        <router-link to="/" class="nav-link">Inicio</router-link>
                    </li>
                    <li class="nav-item">
                        <router-link to="/login" class="nav-link">Mi Cuenta</router-link>
                    </li>
                </ul>
            </div>
        </div>
    </nav>
</template>

<script>
import Login from '../components/Login.vue';

export default {
    name: 'Nav',
    components: {
        Login
    },
}
</script>