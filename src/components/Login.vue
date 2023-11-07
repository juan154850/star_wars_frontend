<template>
    <div class="container mt-5">
        <div class="row">
            <div class="col-md-6 offset-md-3">
                <div v-if="access_token" class="container flex">
                    <button class="btn btn-success" @click="getObjects">Ver personajes</button>
                    <button class="btn btn-danger m-5" @click="logout">Logout</button>
                </div>
                <ul class="list-group mt-3" v-if="objects.length > 0">
                    <li v-for="obj in objects" :key="obj.id" class="list-group-item">{{ obj.name }}</li>
                </ul>
                <div v-if="show_login_form" class="mt-1">
                    <form @submit.prevent="login">
                        <div class="form-group">
                            <label>Email:</label>
                            <input type="email" class="form-control" v-model="email" required>
                        </div>
                        <div class="form-group ">
                            <label>Password:</label>
                            <input type="password" class="form-control" v-model="password" required>
                        </div>
                        <button type="submit" class="btn btn-primary m-3">Login</button>
                    </form>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import 'bootstrap/dist/css/bootstrap.css';
import Login from '../components/Login.vue'


export default {
    name: 'Login',
    data() {
        return {
            objects: [],
            access_token: null,
            refresh_token: null,
            email: '',
            password: '',
            show_login_form: true,
        };
    },
    components: {
        Login,
    },
    mounted() {
        this.checkLogin();
        if (this.access_token) {
            this.show_login_form = false;
        }
    },
    methods: {
        checkLogin() {
            const access_token = localStorage.getItem('access_token');
            const refresh_token = localStorage.getItem('refresh_token');
            if (access_token && refresh_token) {
                this.access_token = access_token;
                this.refresh_token = refresh_token;
            }
        },
        showLoginForm() {
            this.show_login_form = true;
        },
        login() {
            axios.post('http://localhost:8000/api-auth/login/', {
                email: this.email,
                password: this.password
            })
                .then(response => {
                    this.access_token = response.data.access;
                    this.refresh_token = response.data.refresh;
                    localStorage.setItem('access_token', this.access_token);
                    localStorage.setItem('refresh_token', this.refresh_token);
                    this.show_login_form = false;
                })
                .catch(error => {
                    console.log(error);
                });
        },
        logout() {
            localStorage.removeItem('access_token');
            localStorage.removeItem('refresh_token');
            this.access_token = null;
            this.refresh_token = null;
            this.objects = [];
            this.email = '';
            this.password = '';
            this.showLoginForm();
        },
        getObjects() {
            axios.get('http://localhost:8000/api/v1/characters/', {
                headers: {
                    Authorization: `Bearer ${this.access_token}`
                }
            })
                .then(response => {
                    this.objects = response.data.results;
                })
                .catch(error => {
                    console.log(error);
                });
        },
    },
}
</script>