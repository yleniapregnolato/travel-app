<script>
import L from "leaflet";
import "leaflet/dist/leaflet.css";

export default {
    name: "MapView",
    data() {
        return {
            center: [42.4053, 12.8516],
            zoom: 6,
            tileUrl: "https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png",
            tileAttribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors',
            markers: [
                { position: [41.9028, 12.4964], text: "Roma" },
                { position: [45.4408, 12.3155], text: "Venezia" },
                { position: [43.7696, 11.2558], text: "Firenze" },
            ],
        };
    },
    mounted() {
        this.initMap(); 

        this.$nextTick(() => {
            this.initMap();
        });
    },
    methods: {
        initMap() {
            const map = L.map("map").setView(this.center, this.zoom);

            L.tileLayer(this.tileUrl, {
                attribution: this.tileAttribution,
            }).addTo(map);

            this.markers.forEach(marker => {
                L.marker(marker.position)
                    .addTo(map)
                    .bindPopup(marker.text)
                    .openPopup();
            });
        }
    }
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
    border-radius: 30px;
}
</style>