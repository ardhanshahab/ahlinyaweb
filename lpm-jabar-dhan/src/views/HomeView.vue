<script setup>

</script>

<template>
<div class="p-5 mb-4 bg-light rounded-3">
  <div class="container-fluid py-5 row">
    <div class="col-md-6">
      <h1 class="display-5 fw-bold">Selamat Datang di</h1>
      <h1 class="display-5 fw-bold">LPM Jabar</h1>
      <p class="fs-4">Lembaga Pemberdayaan Masyarakat Jawa Barat</p>
      <div class="p-1 m-1">
      <RouterLink class="m-1" v-if="isLoggedIn" to="/createpost">Tambah Data</RouterLink>
      <RouterLink class="m-1" v-if="isLoggedIn" to="/preview">List Data</RouterLink>
      </div>
    </div>
    <div class="col-md-6 position-relative">
      <div class="overlay"></div>
      <img src="https://d22gwcrfo2de51.cloudfront.net/wp-content/uploads/2023/02/19840722-Sejarah-Bandung-scaled.jpg" alt="gedung sate" style="width: 100%;">
    </div>
  </div>
</div>
</template>

<script>
export default {
  data() {
    return {
      isLoggedIn: localStorage.isLoggedIn,
    };
  },
  methods: {
    logout() {
      
      localStorage.removeItem('isLoggedIn');
      this.isLoggedIn = false;
    },
  },
};
</script>

<style scoped>
.overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(255, 255, 255, 0.5); /* Adjust the alpha value for the desired transparency */
}
a {
    background:    #6fa8dc;
    border-radius: 1000px;
    padding:       20px 45px;
    color:         #ffffff;
    display:       inline-block;
    font:          normal bold 26px/1 "Open Sans", sans-serif;
    text-align:    center;
    text-decoration: none;
}

</style>