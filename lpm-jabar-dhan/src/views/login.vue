<template>
  <div class="container-fluid py-2">
    <div class="card p-2" style="width: 30rem;">
      <form @submit.prevent="submitted">
        <div class="text-center">
          <img class="mb-4" src="../assets/logo.svg" alt="" width="72" height="57">
          <h1 class="h3 mb-3 fw-normal">Login</h1>
        </div>
        <div class="form-floating">
          <input v-model="email" type="email" class="form-control" id="floatingInput" placeholder="name@example.com" name="email">
          <label for="floatingInput">Email address</label>
        </div>
        <div class="form-floating">
          <input v-model="password" type="password" class="form-control" id="floatingPassword" placeholder="Password" name="password">
          <label for="floatingPassword">Password</label>
        </div>

        <div class="form-check text-start my-3">
          <input class="form-check-input" type="checkbox" value="remember-me" id="flexCheckDefault">
          <label class="form-check-label" for="flexCheckDefault">
            Remember me
          </label>
        </div>
        <button class="btn btn-primary w-100 py-2" type="submit">Sign in</button>
        <p class="mt-5 mb-3 text-body-secondary">&copy; 2017–2023</p>
      </form>
    </div>
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
