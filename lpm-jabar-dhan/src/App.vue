<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <header>
    <div class="wrapper">
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
        <RouterLink v-if="!isLoggedIn" to="/login">Login</RouterLink>
        <RouterLink v-if="isLoggedIn" to="/" @click="logout">Logout</RouterLink>
      </nav>
    </div>
  </header>
  <div class="body">
    <RouterView />
  </div>
  <footer :class="{ 'floating-footer': isFooterFloating }">
    <p>&copy; 2023 - Ardhan</p>
  </footer>
</template>

<script>
export default {
  data() {
    return {
      isLoggedIn: localStorage.isLoggedIn,
      isFooterFloating: false,
    };
  },
  methods: {
    logout() {
      // Perform logout actions
      // For example, clear localStorage and update isLoggedIn
      localStorage.removeItem('isLoggedIn');
      this.isLoggedIn = false;
    },
    handleScroll() {
      // Check if the page is scrolled beyond a certain point to determine whether the footer should float
      this.isFooterFloating = window.scrollY > 200; // Adjust the value based on your design
    },
  },
  mounted() {
    // Add an event listener to handle scroll events
    window.addEventListener('scroll', this.handleScroll);
    this.handleScroll();
  },
  beforeDestroy() {
    // Remove the event listener when the component is destroyed
    window.removeEventListener('scroll', this.handleScroll);
  },
};

</script>

<style scoped>
header {
  background-color: lightblue;
  line-height: 1.5;
  max-height: 100vh;
}
.body{
  height: 100vh;
}
nav {
  display: flexbox;
  width: 100%;
  font-size: 12px;
  /* text-align: center; */
  margin-top: 2rem;
}

footer{
  position: fixed;
  bottom: 0;
  left: 0;
  padding: 10px;
  color: white;
  background-color: black;
  width: 100%;
  z-index: 1000; 
}

nav a.router-link-exact-active {
  color: var(--color-text);
  color: blue;

}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  /* display: block; */
  color: black;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
  text-decoration: none;
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 500px) {
  header {
    display: grid;
    place-items: center;
    /* padding-right: calc(var(--section-gap) / 2); */
  }

  .logo {
    margin: 0 2rem 0 0;
  }


  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;
    display: flexbox;
    padding: 2rem 0;
    /* margin-top: 1rem; */
  }
}
</style>
