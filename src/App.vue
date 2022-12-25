<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<script>
export default {
  data() {
    return {
      dataMahasiswa: [],
      nama: "",
      nim: "",
    };
  },
  methods: {
    simpanData() {
      var mahasiswa = {
        nama: this.nama,
        nim: this.nim,
      };
      this.dataMahasiswa.push(mahasiswa);
    },
  },
};
</script>

<template>
  <header>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <div class="container-fluid">
        <RouterLink class="navbar-brand" to="/">Navbar</RouterLink>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent"
          aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <li class="nav-item">
              <RouterLink class="nav-link active" aria-current="page" to="/">Home</RouterLink>
            </li>
            <li class="nav-item">
              <RouterLink class="nav-link" to="/about">About</RouterLink>
            </li>
            <li class="nav-item">
              <a class="nav-link disabled" href="#" tabindex="-1" aria-disabled="true">Disabled</a>
            </li>
          </ul>
          <div class="d-flex">
            <button class="btn btn-warning text-white" type="submit">Risky</button>
          </div>
        </div>
      </div>
    </nav>
  </header>
  <RouterView />
  <div class="container mb-5">
    <form>
      <p class="alert alert-warning">Hallo Risky Ariadi Chandra</p>
      <p>Nama</p>
      <input v-model="nama" type="text" class="form-text" />
      <p>Nim</p>
      <input v-model="nim" type="text" class="form-text" />
      <div class="mt-2">
        <button class="btn btn-warning text-white" type="submit" @click.prevent="simpanData">
          Simpan
        </button>
      </div>
    </form>
  </div>
  <div class="container mb-5">
    <table class="table">
      <thead>
        <tr>
          <th>Nama</th>
          <th>Nim</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in dataMahasiswa" :key="item">
          <td>{{ item.nama }}</td>
          <td>{{ item.nim }}</td>
          <button>x</button>
          <button @click.prevent="$delete(item, key)">remove</button>
        </tr>
      </tbody>
    </table>
  </div>

</template>
