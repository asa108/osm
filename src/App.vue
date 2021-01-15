<template>
  <div id="app">
    <div>hello</div>
    <div id="mapid"></div>
  </div>
</template>

<script>
import "leaflet/dist/leaflet.css";
import L from "leaflet";

// デフォルトマーカーアイコン設定
delete L.Icon.Default.prototype._getIconUrl;
L.Icon.Default.mergeOptions({
  iconUrl: require("leaflet/dist/images/marker-icon.png"),
  iconRetinaUrl: require("leaflet/dist/images/marker-icon-2x.png"),
  shadowUrl: require("leaflet/dist/images/marker-shadow.png")
});

export default {
  name: "App",
  mounted() {
    const map = L.map("mapid", {
      center: L.latLng(26.2183, 127.7154),
      zoom: 13
    })
      .addLayer(L.tileLayer("http://{s}.tile.osm.org/{z}/{x}/{y}.png"))
      .on("click", (p) => map.addLayer(L.marker(p.latlng)));
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#mapid {
  height: 500px;
}
</style>
