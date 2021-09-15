<template>
  <div id="app">
    <map-app />
  </div>
</template>

<script>
import MapApp from "@/components/MapApp";

export default {
  name: "App",

  components: {
    MapApp,
  },
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
}
</style>
