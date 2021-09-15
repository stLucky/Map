<template>
  <MglMap
    :accessToken="accessToken"
    :mapStyle="mapOptions.style"
    :attributionControl="false"
    :center="mapOptions.center"
    :zoom="mapOptions.zoom"
    style="width: 100vw; height: 100vh"
  >
    <MglGeojsonLayer
      :sourceId="geoJsonSource.data.id"
      :source="geoJsonSource"
      layerId="myLayer"
      :layer="geoJsonLayer"
    />
  </MglMap>
</template>
<script>
import "mapbox-gl/dist/mapbox-gl.css";
import Mapbox from "mapbox-gl";
import { MglMap, MglGeojsonLayer } from "vue-mapbox";

export default {
  name: "MapApp",

  components: {
    MglMap,
    MglGeojsonLayer,
  },

  data: () => ({
    accessToken:
      "pk.eyJ1Ijoic3RsdWNra3kiLCJhIjoiY2t0a2FveWFnMDQ3azJ1cHFyOTl0dWFrcyJ9.UdXyRDEInJ8IufMk4z0pPQ",

    mapOptions: {
      style: "mapbox://styles/mapbox/streets-v11",
      center: [37.62, 55.75],
      zoom: 16,
    },

    geoJsonSource: {
      type: "geojson",
      data: {
        id: "polygon",
        type: "Feature",
        geometry: {
          type: "Polygon",
          coordinates: [
            [
              [37.618610077382044, 55.750976522976856],
              [37.616848273079, 55.749336368113006],
              [37.62308744471318, 55.74973895796529],
              [37.621497846844335, 55.75248242262731],
              [37.618610077382044, 55.750976522976856],
            ],
          ],
        },
      },
    },

    geoJsonLayer: {
      type: "fill",
      paint: {
        "fill-color": "#0080ff",
        "fill-opacity": 0.5,
        "fill-outline-color": "#000000",
      },
    },
  }),

  created() {
    this.mapbox = Mapbox;
  },
};
</script>
