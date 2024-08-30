<script>
import L from "leaflet";
import "leaflet/dist/leaflet.css";

export default {
  name: "MapView",
  data() {
    return {
      center: [45.4642, 9.1900],
      zoom: 13,
      tileUrl: "https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png",
      tileAttribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors',
      markerPosition: [45.4642, 9.1900],
      markerText: "Milano!"
    };
  },
  mounted() {
    this.initMap();
  },
  methods: {
    initMap() {
      const map = L.map("map").setView(this.center, this.zoom);

      L.tileLayer(this.tileUrl, {
        attribution: this.tileAttribution,
      }).addTo(map);

      L.marker(this.markerPosition)
        .addTo(map)
        .bindPopup(this.markerText)
        .openPopup();
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