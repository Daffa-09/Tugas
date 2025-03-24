<script setup>
import { ref, watch } from "vue";

console.info("Vue Running");

const title = ref("Penghitungan nilai");
const nama = ref("");
const nilai = ref(50); 
const warna = ref("black");


const kategoriNilai = () => {
  if (nilai.value < 50) return "Kurang";
  else if (nilai.value  >= 50 && nilai.value < 80) return "Cukup";
  else return "Baik";
};


watch(nilai, (newValue) => {
  if (newValue < 50) warna.value = "red";
  else if (newValue >= 50 && newValue < 80) warna.value = "orange";
  else warna.value = "green";
});
</script>

<template>
  <div>
    <h1>{{ title }}</h1>

   
    <input type="text" v-model="nama" placeholder="Masukkan nama Anda">
    <p>Halo, {{ nama || "Pengguna" }}!</p>

   
    <label>Masukkan nilai Anda:</label>
    <input type="number" v-model="nilai" min="0" max="100">

   
    <p>Nilai Anda: {{ nilai }}</p>
    <p :style="{ color: warna }">Kategori: {{ kategoriNilai() }}</p>
  </div>
</template>