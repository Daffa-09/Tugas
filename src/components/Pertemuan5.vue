<script setup>
import { ref, watch, computed, onMounted } from "vue";

console.info("Vue Running");

const title = ref("Penghitungan nilai");
const nama = ref("");
const nilai = ref(50);
const warna = ref("black");


const kategoriNilai = computed(() => {
  if (nilai.value < 50) return "Kurang";
  else if (nilai.value >= 50 && nilai.value < 80) return "Cukup";
  else return "Baik";
});


watch(nilai, (newValue) => {
  if (newValue < 50) warna.value = "red";
  else if (newValue >= 50 && newValue < 80) warna.value = "orange";
  else warna.value = "green";
});


const daftarNilai = ref([
  { id: 1, nama: "Daffa", nilai: 80 },
  { id: 2, nama: "Erfin", nilai: 50 },
  { id: 3, nama: "Budi", nilai: 30 }
]);
onMounted(() =>{
  console.log("Data telah Diinputkan")
}
)

</script>

<template>
  <div>
    <h1>{{ title }}</h1>

    <input type="text" v-model="nama" placeholder="Masukkan nama Anda">
    <p>Halo, {{ nama || "Pengguna" }}!</p>

    <label>Masukkan nilai Anda:</label>
    <input type="number" v-model="nilai" min="0" max="100">

    <p>Nilai Anda: {{ nilai }}</p>
    <p :style="{ color: warna }">Kategori: {{ kategoriNilai }}</p>
    <h2>Daftar Nilai</h2>
    <u1>
      <li v-for="item in daftarNilai" :key="item.id">
        {{ item.nama }} : {{ item.nilai }} ({{ 
          item.nilai<50 ? 'Kurang' : item.nilai <80 ? 'Cukup':'Baik' }})
      </li>
    </u1>
  </div>
</template>
