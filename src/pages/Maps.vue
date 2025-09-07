<script setup>
import L from "leaflet";
import "leaflet/dist/leaflet.css";
import { onMounted } from "vue";
let map = null;

onMounted(() => {
  map = L.map("map").setView([51.505, -0.09], 13);
  L.tileLayer("https://tile.openstreetmap.org/{z}/{x}/{y}.png", {
    maxZoom: 19,
    attribution:
      '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>',
  }).addTo(map);
});

function goTo(coords, zoom){ 
    map.flyTo(coords, zoom) 
}
</script>

<template>
  <button class="button is-primary" @click="goTo([59.4047, 24.6765], 19)">Go To Alcohol</button>
  <div id="map"></div>
</template>

<style scoped>
#map {
  height: 90vh;
}
</style>
