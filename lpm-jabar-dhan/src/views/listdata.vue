<template>
  <div class="container-fluid py-2">
    
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      isLoggedIn: true
    };
  },
  methods: {
    submitted() {
      if (this.email === "admin@gmail.com" && this.password === "admin") {
        this.$router.push({ name: "home" });
        localStorage.isLoggedIn = this.isLoggedIn;
        // localStorage.setItem('isLoggedIn') === 'true';
      } else {
        alert("Invalid credentials"); // alert
      localStorage.removeItem('isLoggedIn');
      }
    },
  },
};
</script>

<style>
.card{
  padding: 10px;
  margin: auto;
}

.form-signin {
  max-width: 330px;
  padding: 1rem;
}

.form-signin .form-floating:focus-within {
  z-index: 2;
}

.form-signin input[type="email"] {
  margin-bottom: -1px;
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}

.form-signin input[type="password"] {
  margin-bottom: 10px;
  border-top-left-radius: 0;
  border-top-right-radius: 0;
}
</style>
