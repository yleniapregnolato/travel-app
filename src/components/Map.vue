<script>
import { onMounted } from "vue";
import L from "leaflet";
import "leaflet/dist/leaflet.css";

export default {
    name: "MapView",
    setup() {
        onMounted(() => {
            const map = L.map("map").setView([45.4642, 9.1900], 13);

            L.tileLayer("https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png", {
                attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors',
            }).addTo(map);

            L.marker([41.9028, 12.4964])
                .addTo(map)
                .bindPopup("Roma")
                .openPopup();
        });
    },
};
</script>

<template>
    <div id="map"></div>
</template>
  
<style scoped lang="scss">

#map {
    height: 500px;
    width: 50%;
    position: relative;
    bottom: 600px;
    margin-left: 40px;
}
</style>