<template>
    <div class="container mt-5">
        <div class="row">
            <div class="col-md-6 offset-md-3">
                <div v-if="access_token" class="container flex">
                    <button class="btn btn-success m-2" @click="getCharacters">View Characters</button>
                    <button class="btn btn-success m-2" @click="getFilms">View Films</button>
                    <button class="btn btn-success m-2" @click="getPlanets">Vies Planets</button>
                    <button class="btn btn-danger m-2" @click="logout">Logout</button>
                </div>
                <div v-if="characters.length > 0" class="row row-cols-1 g-4">
                    <div class="col" v-for="character in characters" :key="character.id">
                        <div class="card-group ">
                            <div class="card">
                                <img class="card-img-top" :src="character.picture" alt="image of the character">
                                <div class="card-body text-center">
                                    <h5 class="card-title"><strong>{{ character.name }}</strong></h5>
                                    <div class="d-flex row row-cols-3">
                                        <p class="card-text">
                                            <svg xmlns="http://www.w3.org/2000/svg" width="35" height="35"
                                                fill="currentColor" class="bi bi-cake2-fill" viewBox="0 0 16 16">
                                                <path
                                                    d="m2.899.804.595-.792.598.79A.747.747 0 0 1 4 1.806v4.886c-.354-.06-.689-.127-1-.201V1.813a.747.747 0 0 1-.1-1.01ZM13 1.806v4.685a15.19 15.19 0 0 1-1 .201v-4.88a.747.747 0 0 1-.1-1.007l.595-.792.598.79A.746.746 0 0 1 13 1.806Zm-3 0a.746.746 0 0 0 .092-1.004l-.598-.79-.595.792A.747.747 0 0 0 9 1.813v5.17c.341-.013.675-.031 1-.055V1.806Zm-3 0v5.176c-.341-.012-.675-.03-1-.054V1.813a.747.747 0 0 1-.1-1.01l.595-.79.598.789A.747.747 0 0 1 7 1.806Z" />
                                                <path
                                                    d="M4.5 6.988V4.226a22.6 22.6 0 0 1 1-.114V7.16c0 .131.101.24.232.25l.231.017c.332.024.672.043 1.02.055l.258.01a.25.25 0 0 0 .26-.25V4.003a29.015 29.015 0 0 1 1 0V7.24a.25.25 0 0 0 .258.25l.259-.009c.347-.012.687-.03 1.019-.055l.231-.017a.25.25 0 0 0 .232-.25V4.112c.345.031.679.07 1 .114v2.762a.25.25 0 0 0 .292.246l.291-.049c.364-.061.71-.13 1.033-.208l.192-.046a.25.25 0 0 0 .192-.243V4.621c.672.184 1.251.409 1.677.678.415.261.823.655.823 1.2V13.5c0 .546-.408.94-.823 1.201-.44.278-1.043.51-1.745.696-1.41.376-3.33.603-5.432.603-2.102 0-4.022-.227-5.432-.603-.702-.187-1.305-.418-1.745-.696C.408 14.44 0 14.046 0 13.5v-7c0-.546.408-.94.823-1.201.426-.269 1.005-.494 1.677-.678v2.067c0 .116.08.216.192.243l.192.046c.323.077.669.147 1.033.208l.292.05a.25.25 0 0 0 .291-.247ZM1 8.82v1.659a1.935 1.935 0 0 0 2.298.43.935.935 0 0 1 1.08.175l.348.349a2 2 0 0 0 2.615.185l.059-.044a1 1 0 0 1 1.2 0l.06.044a2 2 0 0 0 2.613-.185l.348-.348a.938.938 0 0 1 1.082-.175c.781.39 1.718.208 2.297-.426V8.833l-.68.907a.938.938 0 0 1-1.17.276 1.938 1.938 0 0 0-2.236.363l-.348.348a1 1 0 0 1-1.307.092l-.06-.044a2 2 0 0 0-2.399 0l-.06.044a1 1 0 0 1-1.306-.092l-.35-.35a1.935 1.935 0 0 0-2.233-.362.935.935 0 0 1-1.168-.277L1 8.82Z" />
                                            </svg>
                                            <strong>Age:</strong> {{ character.age }}
                                        </p>
                                        <p class="card-text">
                                            <svg xmlns="http://www.w3.org/2000/svg" width="35" height="35"
                                                fill="currentColor" class="bi bi-gender-neuter" viewBox="0 0 16 16">
                                                <path fill-rule="evenodd"
                                                    d="M8 1a4 4 0 1 0 0 8 4 4 0 0 0 0-8ZM3 5a5 5 0 1 1 5.5 4.975V15.5a.5.5 0 0 1-1 0V9.975A5 5 0 0 1 3 5Z" />
                                            </svg>
                                            <strong>Gender:</strong> {{ character.gender }}
                                        </p>
                                        <p class="card-text">
                                            <svg xmlns="http://www.w3.org/2000/svg" width="35" height="35"
                                                fill="currentColor" class="bi bi-palette" viewBox="0 0 16 16">
                                                <path
                                                    d="M8 5a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3zm4 3a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3zM5.5 7a1.5 1.5 0 1 1-3 0 1.5 1.5 0 0 1 3 0zm.5 6a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3z" />
                                                <path
                                                    d="M16 8c0 3.15-1.866 2.585-3.567 2.07C11.42 9.763 10.465 9.473 10 10c-.603.683-.475 1.819-.351 2.92C9.826 14.495 9.996 16 8 16a8 8 0 1 1 8-8zm-8 7c.611 0 .654-.171.655-.176.078-.146.124-.464.07-1.119-.014-.168-.037-.37-.061-.591-.052-.464-.112-1.005-.118-1.462-.01-.707.083-1.61.704-2.314.369-.417.845-.578 1.272-.618.404-.038.812.026 1.16.104.343.077.702.186 1.025.284l.028.008c.346.105.658.199.953.266.653.148.904.083.991.024C14.717 9.38 15 9.161 15 8a7 7 0 1 0-7 7z" />
                                            </svg>
                                            <strong>Skin Color:</strong> {{ character.skin_color }}
                                        </p>
                                        <p class="card-text">
                                            <svg xmlns="http://www.w3.org/2000/svg" width="35" height="35"
                                                fill="currentColor" class="bi bi-eye" viewBox="0 0 16 16">
                                                <path
                                                    d="M16 8s-3-5.5-8-5.5S0 8 0 8s3 5.5 8 5.5S16 8 16 8zM1.173 8a13.133 13.133 0 0 1 1.66-2.043C4.12 4.668 5.88 3.5 8 3.5c2.12 0 3.879 1.168 5.168 2.457A13.133 13.133 0 0 1 14.828 8c-.058.087-.122.183-.195.288-.335.48-.83 1.12-1.465 1.755C11.879 11.332 10.119 12.5 8 12.5c-2.12 0-3.879-1.168-5.168-2.457A13.134 13.134 0 0 1 1.172 8z" />
                                                <path
                                                    d="M8 5.5a2.5 2.5 0 1 0 0 5 2.5 2.5 0 0 0 0-5zM4.5 8a3.5 3.5 0 1 1 7 0 3.5 3.5 0 0 1-7 0z" />
                                            </svg>
                                            <strong>Eye Color:</strong> {{ character.eye_color }}
                                        </p>
                                        <p class="card-text">
                                            <svg xmlns="http://www.w3.org/2000/svg" width="35" height="35"
                                                fill="currentColor" class="bi bi-person-arms-up" viewBox="0 0 16 16">
                                                <path d="M8 3a1.5 1.5 0 1 0 0-3 1.5 1.5 0 0 0 0 3Z" />
                                                <path
                                                    d="m5.93 6.704-.846 8.451a.768.768 0 0 0 1.523.203l.81-4.865a.59.59 0 0 1 1.165 0l.81 4.865a.768.768 0 0 0 1.523-.203l-.845-8.451A1.492 1.492 0 0 1 10.5 5.5L13 2.284a.796.796 0 0 0-1.239-.998L9.634 3.84a.72.72 0 0 1-.33.235c-.23.074-.665.176-1.304.176-.64 0-1.074-.102-1.305-.176a.72.72 0 0 1-.329-.235L4.239 1.286a.796.796 0 0 0-1.24.998l2.5 3.216c.317.316.475.758.43 1.204Z" />
                                            </svg>
                                            <strong>height (cm):</strong> {{ character.height }}
                                        </p>
                                        <p class="card-text">
                                            <svg xmlns="http://www.w3.org/2000/svg" width="35" height="35"
                                                fill="currentColor" class="bi bi-hammer" viewBox="0 0 16 16">
                                                <path
                                                    d="M9.972 2.508a.5.5 0 0 0-.16-.556l-.178-.129a5.009 5.009 0 0 0-2.076-.783C6.215.862 4.504 1.229 2.84 3.133H1.786a.5.5 0 0 0-.354.147L.146 4.567a.5.5 0 0 0 0 .706l2.571 2.579a.5.5 0 0 0 .708 0l1.286-1.29a.5.5 0 0 0 .146-.353V5.57l8.387 8.873A.5.5 0 0 0 14 14.5l1.5-1.5a.5.5 0 0 0 .017-.689l-9.129-8.63c.747-.456 1.772-.839 3.112-.839a.5.5 0 0 0 .472-.334z" />
                                            </svg>
                                            <strong>Mass (kg):</strong> {{ character.mass }}
                                        </p>
                                    </div>
                                </div>
                                <div class="text-left">
                                    <p class="card-text"><strong>Appears in the films:</strong></p>
                                    <div class="d-flex justify-content-between row row-cols-2">
                                        <p v-for="film in character.peliculas" :key="film.id">
                                            - {{ film.title }}
                                        </p>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                <div v-if="films.length > 0" class="row row-cols-1 g-4">
                    <div class="col " v-for="film in films" :key="film.id">
                        <div class="card-group ">
                            <div class="card ">
                                <!-- <img class="card-img-top" :src="film.picture" alt="image of the character" /> -->
                                <div class="card-body">
                                    <h5 class="card-title"><strong>{{ film.title }}</strong></h5>
                                    <div class="d-flex row row-cols-1 films-content">
                                        <p class="card-text">
                                            <strong>Description:</strong> {{ film.opening_crawl }}
                                        </p>
                                        <p class="card-text">
                                            <strong>Release date:</strong> {{ film.release_date }}
                                        </p>
                                        <p class="card-text"><strong>Directors:</strong>
                                        <div class="d-flex justify-content-between row row-cols-2">
                                            <p v-for="director in film.directors" :key="director.index">
                                                - {{ director }}
                                            </p>
                                        </div>
                                        </p>
                                        <p class="card-text"><strong>Producers:</strong>
                                        <div class="d-flex justify-content-between row row-cols-2">
                                            <p v-for="producer in film.producers" :key="producer.index">
                                                - {{ producer }}
                                            </p>
                                        </div>
                                        </p>
                                        <p class="card-text"><strong>Planets in this film:</strong>
                                        <div class="d-flex justify-content-between row row-cols-2">
                                            <p v-for="planets in film.planetas" :key="planets.id">
                                                - {{ planets.name }}
                                            </p>
                                        </div>
                                        </p>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                <div v-if="planets.length > 0" class="row row-cols-1 g-4">
                    <div class="col" v-for="planet in planets" :key="planet.id">
                        <div class="card-group">
                            <div class="card">
                                <!-- <img class="card-img-top" :src="planet.picture" alt="image of the planet" /> -->
                                <div class="card-body text-center">
                                    <h5 class="card-title"><strong>{{ planet.name }}</strong></h5>
                                    <div class="d-flex row row-cols-3">
                                        <p class="card-text">
                                            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16"
                                                fill="currentColor" class="bi bi-rulers" viewBox="0 0 16 16">
                                                <path
                                                    d="M1 0a1 1 0 0 0-1 1v14a1 1 0 0 0 1 1h5v-1H2v-1h4v-1H4v-1h2v-1H2v-1h4V9H4V8h2V7H2V6h4V2h1v4h1V4h1v2h1V2h1v4h1V4h1v2h1V2h1v4h1V1a1 1 0 0 0-1-1H1z" />
                                            </svg>
                                            <strong>Diameter:</strong> {{ planet.diameter }}
                                        </p>
                                        <p class="card-text">
                                            <img width="25" height="25"
                                                src="https://img.icons8.com/pulsar-line/25/severity.png" alt="severity"
                                                class="custom-img" />
                                            <strong>Gravity:</strong> {{ planet.gravity }} 
                                        </p>
                                        <p class="card-text">
                                            <img width="20" height="20"
                                                src="https://img.icons8.com/external-becris-lineal-becris/20/external-population-environment-becris-lineal-becris.png"
                                                alt="external-population-environment-becris-lineal-becris"
                                                class="custom-img" />
                                            <strong>Population:</strong> {{ planet.population }}
                                        </p>
                                        <p class="card-text">
                                            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16"
                                                fill="currentColor" class="bi bi-cloud-sun" viewBox="0 0 16 16">
                                                <path
                                                    d="M7 8a3.5 3.5 0 0 1 3.5 3.555.5.5 0 0 0 .624.492A1.503 1.503 0 0 1 13 13.5a1.5 1.5 0 0 1-1.5 1.5H3a2 2 0 1 1 .1-3.998.5.5 0 0 0 .51-.375A3.502 3.502 0 0 1 7 8zm4.473 3a4.5 4.5 0 0 0-8.72-.99A3 3 0 0 0 3 16h8.5a2.5 2.5 0 0 0 0-5h-.027z" />
                                                <path
                                                    d="M10.5 1.5a.5.5 0 0 0-1 0v1a.5.5 0 0 0 1 0v-1zm3.743 1.964a.5.5 0 1 0-.707-.707l-.708.707a.5.5 0 0 0 .708.708l.707-.708zm-7.779-.707a.5.5 0 0 0-.707.707l.707.708a.5.5 0 1 0 .708-.708l-.708-.707zm1.734 3.374a2 2 0 1 1 3.296 2.198c.199.281.372.582.516.898a3 3 0 1 0-4.84-3.225c.352.011.696.055 1.028.129zm4.484 4.074c.6.215 1.125.59 1.522 1.072a.5.5 0 0 0 .039-.742l-.707-.707a.5.5 0 0 0-.854.377zM14.5 6.5a.5.5 0 0 0 0 1h1a.5.5 0 0 0 0-1h-1z" />
                                            </svg>
                                            <strong>Climate:</strong> {{ planet.climate }}
                                        </p>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>

                </div>
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
            characters: [],
            films: [],
            planets: [],
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
            this.characters = [];
            this.films = [];
            this.planets = [];
            this.email = '';
            this.password = '';
            this.showLoginForm();
        },
        getCharacters() {
            this.films = [];
            this.planets = [];
            axios.get('http://localhost:8000/api/v1/characters/', {
                headers: {
                    Authorization: `Bearer ${this.access_token}`
                }
            })
                .then(response => {
                    this.characters = response.data.results;
                })
                .catch(error => {
                    console.log(error);
                });
        },
        getFilms() {
            this.characters = [];
            this.planets = [];
            axios.get('http://localhost:8000/api/v1/films/', {
                headers: {
                    Authorization: `Bearer ${this.access_token}`
                }
            })
                .then(response => {
                    this.films = response.data.results;
                })
                .catch(error => {
                    console.log(error);
                });
        },
        getPlanets() {
            this.characters = [];
            this.films = [];
            axios.get('http://localhost:8000/api/v1/planets/', {
                headers: {
                    Authorization: `Bearer ${this.access_token}`
                }
            })
                .then(response => {
                    this.planets = response.data.results;
                })
                .catch(error => {
                    console.log(error);
                });
        },
    },
}
</script>

<style>
svg,
.custom-img {
    margin-right: 10px;
    width: 20px;
    height: 20px;
}

.films-content {
    text-align: left;
}</style>