<template>
  <div id="app">
    <nav class="navbar navbar-expand-lg navbar-light bg-light mb-5">
      <div class="container-fluid">
        <a class="navbar-brand"
        href="#"
        @click.prevent="goHome"
        >Modemarkt</a>
        <button
          class="navbar-toggler"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarSupportedContent"
          aria-controls="navbarSupportedContent"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <!-- <li class="nav-item mx-2">
              <router-link to="/" class="text-decoration-none text-dark"
                >Home</router-link
              >
            </li> -->
            <li class="nav-item mx-2">
              <router-link
                to="/products"
                class="text-decoration-none text-dark"
                v-if="isLoggedIn"
                >Products
              </router-link>
            </li>
            <li class="nav-item mx-2" >
              <router-link
                to="/login"
                class="text-decoration-none text-dark"
                v-if="!isLoggedIn"
                >Login
              </router-link>
            </li>
            <li class="nav-item mx-2 ">
              <a href=""
              @click.prevent="logout"
              v-if="isLoggedIn"
              class="text-decoration-none text-dark"
              >Logout</a>
            </li>

          </ul>
        </div>
      </div>
    </nav>

    <router-view />

  </div>
</template>

<script>
// @ is an alias to /src
// import { mapState } from 'vuex'

export default {
  name: 'App',
  data () {
    return {
      productList: []
    }
  },
  methods: {
    goHome () {
      this.$router.push({ path: '/' })
    },
    logout () {
      localStorage.clear()
      this.$router.push({ path: '/' })
    }
  },
  created () {
  },
  computed: {
    isLoggedIn () {
      return this.$store.state.isLoggedIn
    }
  }
}
</script>

<style>
#app {
  /* font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50; */
}
</style>
