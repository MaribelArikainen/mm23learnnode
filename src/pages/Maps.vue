<script setup>
import L from "leaflet";
import "leaflet/dist/leaflet.css";
import 'leaflet/dist/images/marker-icon.png';
import 'leaflet/dist/images/marker-shadow.png';
import { onMounted } from "vue";
let map = null;

onMounted(() => {
  map = L.map("map").setView([51.505, -0.09], 13);
  L.tileLayer("https://tile.openstreetmap.org/{z}/{x}/{y}.png", {
    maxZoom: 19,
    attribution:
      '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>',
  }).addTo(map);

  var polygon = L.polygon([
    [59.40663, 24.67768],
    [59.40663, 24.67788],
    [59.40652, 24.67788],
    [59.40652, 24.67768]
    
    ]).addTo(map);
  let marker1 = L.marker([51.5, -0.09]).addTo(map);
  let marker2 = L.marker([59.4047, 24.6765]).addTo(map);
  let marker3 = L.marker([59.406575, 24.67778]).addTo(map);
});

function goTo(coords, zoom){ 
    map.flyTo(coords, zoom) 
}
</script>

<template>
    <div class="field has-addons">
        <div class="control">
            <button class="button is-primary" @click="goTo([59.4047, 24.6765], 19)">Go To Alcohol</button>
        </div>
        <div class="control">
            <button class="button is-primary" @click="goTo([59.406575, 24.67778], 19)">Go To Home</button>
        </div>
    </div>
  <div id="map"></div>
</template>

<style scoped>
#map {
  height: 90vh;
}
</style>
