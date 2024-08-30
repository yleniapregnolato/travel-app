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
                { position: [41.9028, 12.4964], text: "Roma", img: "/src/assets/img/carbonara.jpeg" },
                { position: [45.4408, 12.3155], text: "Venezia", img: "/src/assets/img/baccalà.jpeg" },
                { position: [43.7696, 11.2558], text: "Firenze", img: "/src/assets/img/fiorentina.jpeg" },
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
                const popupContent = `
                    <div>
                        <h3>${marker.text}</h3>
                        <img src="${marker.img}" alt="${marker.text}" style="width:200px;height:auto;">
                    </div>
                `;
                L.marker(marker.position)
                    .addTo(map)
                    .bindPopup(popupContent);
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
    height: 550px;
    width: 80%;
    position: relative;
    bottom: 650px;
    border-radius: 30px;
    margin: 0 auto;
}
</style>