<template>
  <div class="container-fluid py-2">
    <div class="card" style="width: auto;">
        <div class="card-header">
          <h4>Tambah Data</h4>
        </div>
        <div class="card-body">
          <form @submit.prevent="kirimData">
            <div class="form-floating">
              <input v-model="nama" type="text" class="form-control" id="floatingInput" placeholder="Nama" name="nama">
              <label for="floatingInput">Nama</label>
            </div>
            <div class="form-floating">
              <input v-model="nik" type="number" class="form-control" id="floatingInput" placeholder="NIK" name="nik">
              <label for="floatingInput">NIK</label>
            </div>
            <div class="form-floating">
              <input v-model="nokk" type="number" class="form-control" id="floatingInput" placeholder="No Kartu Keluarga" name="nokk">
              <label for="floatingInput">No Kartu Keluarga</label>
            </div>
            <div class="input-group">
              <label class="input-group-text" for="fotoktp">Foto KTP</label>
              <input type="file" class="form-control" id="fotoktp" name="fotoktp">
            </div>
            <div class="form-floating">
              <input v-model="umur" type="number" @blur="validateUmur" class="form-control" id="floatingInput" placeholder="Umur" name="umur">
              <label for="floatingInput">Umur</label>
            </div>
            <div class="input-group">
              <label class="input-group-text" for="jk">Jenis Kelamin</label>
              <select class="form-select" id="jk" name="jk" v-model="jk">
                <option selected>Pilih</option>
                <option value="L">Laki-laki</option>
                <option value="P">Perempuan</option>
                <!-- <option value="3">Three</option> -->
              </select>
            </div>
            <div class="input-group">
              <label class="input-group-text" for="provinsi">Provinsi</label>
              <select class="form-select" id="provinsi" name="provinsi" @change="provinsiChanged" v-model="provinsi">
                <option value="" selected>Pilih</option>
                <option v-for="provinsi in provinsiList" :key="provinsi.id" :value="provinsi.id">{{ provinsi.name }}</option>
              </select>
            </div>
            <div class="input-group">
              <label class="input-group-text" for="kota">Kab/Kota</label>
              <select class="form-select" id="kota" name="kota" @change="kotaChanged" v-model="kota">
                <option value="" selected>Pilih</option>
                <option v-for="kota in kotaList" :key="kota.id" :value="kota.id">{{ kota.name }}</option>
              </select>
            </div>
            <div class="input-group ">
              <label class="input-group-text" for="kecamatan">Kecamatan</label>
              <select class="form-select" id="kecamatan" name="kecamatan" @change="kecamatanChanged" v-model="kecamatan">
                <option value="" selected>Pilih</option>
                <option v-for="kecamatan in kecamatanList" :key="kecamatan.id" :value="kecamatan.id">{{ kecamatan.name }}</option>
              </select>
            </div>
            <div class="input-group ">
              <label class="input-group-text" for="desa">Kelurahan / Desa</label>
              <select class="form-select" id="desa" name="desa" v-model="desa">
                <option value="" selected>Pilih</option>
                <option v-for="desa in desaList" :key="desa.id" :value="desa.id">{{ desa.name }}</option>
                <!-- <option value="3">Three</option> -->
              </select>
            </div>
            <div class="form-floating">
              <input v-model="alamat" @blur="validateAlamat" type="text" class="form-control" id="floatingInput" placeholder="Alamat" name="alamat">
              <label for="floatingInput">Alamat</label>
            </div>
            <div class="form-floating">
              <input v-model="rt" type="number" class="form-control" id="floatingInput" placeholder="RT" name="rt">
              <label for="floatingInput">RT</label>
            </div>
            <div class="form-floating">
              <input v-model="rw" type="number" class="form-control" id="floatingInput" placeholder="RW" name="rw">
              <label for="floatingInput">RW</label>
            </div>
            <div class="form-floating">
              <input v-model="beforecov" type="number" class="form-control" id="floatingInput" placeholder="Penghasilan Sebelum Pandemi" name="beforecov">
              <label for="floatingInput">Penghasilan Sebelum Pandemi</label>
            </div>
            <div class="form-floating">
              <input v-model="aftercov" type="number" class="form-control" id="floatingInput" placeholder="Penghasilan Sesudah Pandemi" name="aftercov">
              <label for="floatingInput">Penghasilan Sesudah Pandemi</label>
            </div>
            <div class="form-floating">
              <input v-model="alasan" type="text" class="form-control" id="floatingInput" placeholder="Alasan Membutuhkan Bantuan" name="alasan">
              <label for="floatingInput">Alasan Membutuhkan Bantuan</label>
            </div>
            <div class="form-check text-start my-3">
              <input class="form-check-input" type="checkbox" value="true" v-model="pernyataanCeklis" id="flexCheckDefault" name="pernyataan">
              <label class="form-check-label" for="flexCheckDefault">
                Saya menyatakan bahwa data yang diisikan adalah benar dan siap dipertanggungjawabkan apabila ditemukan ketidaksesuaian dalam data tersebut
              </label>
            </div>
            <button class="btn btn-primary w-100 py-2" type="submit" :disabled="!pernyataanCeklis">Send</button>
            <p class="mt-5 mb-3 text-body-secondary">&copy; 2017–2023</p>
          </form>
        </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
// import PreviewTable from './PreviewTable.vue'; // Import the new component

export default {
  // components: {
  //   PreviewTable,
  // },
  data() {
    return {
      pernyataanCeklis: false,
      submittedData: {},
      showPreview: false,
      nama: "",
      nik: null,
      nokk: null,
      umur: null,
      fotoktp: "",
      jk: "",
      provinsiList: [],
      kota: "",
      provinsi: "",
      kotaList: [],
      kecamatanList: [],
      kecamatan: "",
      desaList: [],
      desa: "",
      alamat: "",
      rt: "",
      rw: "",
      beforecov: "",
      aftercov: "",
      alasan: "",
      alamatError: "",
    };
  },
  computed:{
    
  },
  mounted() {
    this.fetchprovinsi();
    this.fetchkota();
    this.fetchkecamatan();
    this.fetchdesa();
  },
  methods: {
    async fetchprovinsi() {
      try {
        const response = await axios.get('https://www.emsifa.com/api-wilayah-indonesia/api/provinces.json');
        this.provinsiList = response.data;
      } catch (error) {
        console.error('Error fetching provinces:', error);
      }
    },
    async fetchkota() {
      if (this.provinsi) {
        try {
          const response = await axios.get(`https://www.emsifa.com/api-wilayah-indonesia/api/regencies/${this.provinsi}.json`);
          this.kotaList = response.data;
        } catch (error) {
          console.error('Error fetching cities:', error);
        }
      }
    },
    async fetchkecamatan() {
      if (this.kota) {
        try {
          const response = await axios.get(`https://www.emsifa.com/api-wilayah-indonesia/api/districts/${this.kota}.json`);
          this.kecamatanList = response.data;
        } catch (error) {
          console.error('Error fetching cities:', error);
        }
      }
    },
    async fetchdesa() {
      if (this.kecamatan) {
        try {
          const response = await axios.get(`https://www.emsifa.com/api-wilayah-indonesia/api/villages/${this.kecamatan}.json`);
          this.desaList = response.data;
        } catch (error) {
          console.error('Error fetching cities:', error);
        }
      }
    },

    provinsiChanged() {
      this.fetchkota();
    },
    kotaChanged() {
      this.fetchkecamatan();
    },
    kecamatanChanged() {
      this.fetchdesa();
    },
    validateUmur() {
      if (this.umur !== null && this.umur < 24) {
        this.umurError = "Umur harus 25 tahun atau lebih";
      } else {
        this.umurError = "";
      }
    },
    validateAlamat() {
      const maxAlamatLength = 255;
      if (this.alamat.length > maxAlamatLength) {
        this.alamatError = `Alamat tidak boleh lebih dari ${maxAlamatLength} karakter`;
      } else {
        this.alamatError = "";
      }
    },

    async kirimData() {
      const randomTimeout = Math.floor(Math.random() * (3000 - 1000 + 1)) + 1000;
      await this.sleep(randomTimeout);
      console.log(randomTimeout);
      localStorage.setItem('loading', randomTimeout.toString());

      if (this.umurError) {
        alert(this.umurError);
        return;
      }
      if (this.alamatError) {
        alert(this.alamatError);
        return;
      }

      const formData = {
        nama: this.nama,
        nik: this.nik,
        nokk: this.nokk,
        umur: this.umur,
        fotoktp: this.fotoktp,
        jk: this.jk,
        provinsi: this.provinsi,
        kota: this.kota,
        kecamatan: this.kecamatan,
        desa: this.desa,
        alamat: this.alamat,
        rt: this.rt,
        rw: this.rw,
        beforecov: this.beforecov,
        aftercov: this.aftercov,
        alasan: this.alasan,
      };

      const formDataString = JSON.stringify(formData);

      localStorage.setItem('submittedData', formDataString);

      this.submittedData = formData;
      this.showPreview = true;

      console.log('Sending data to server:', formData);
      console.log(this.showPreview);

      this.$router.push({
        path: '/preview',
        props: {
          submittedData: formData,
          showPreview: this.showPreview,
        },
      });
      },
      sleep(ms) {
    return new Promise(resolve => setTimeout(resolve, ms));
  },
  clearForm() {
    
    this.nama = "";
    this.nik = null;
    this.nokk = null;
    this.umur = null;
    this.fotoktp = "";
    this.jk = "";
    this.provinsi = "";
    this.kota = "";
    this.kecamatan = "";
    this.desa = "";
    this.alamat = "";
    this.rt = "";
    this.rw = "";
    this.beforecov = "";
    this.aftercov = "";
    this.alasan = "";
    },
    },
  };
</script>

<style>
.card{
  padding: 10px;
  margin: auto;
}

</style>
