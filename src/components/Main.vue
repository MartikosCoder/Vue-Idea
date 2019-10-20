<template>
  <div class="main">
    {{ msg }}
    <div class="latitude">Latitude: {{ latitude }}</div>
    <div class="longitude">Longitude: {{ longitude }}</div>
  </div>
</template>

<script>
export default {
  name: 'Main',
  props: {
    msg: String
  },
  data() {
    return {
      latitude: 0,
      longitude: 0
    }
  },
  methods: {
    getCoords() {
      if (navigator.geolocation) {
        const _this = this;
        navigator.geolocation.getCurrentPosition(position => {
          _this.latitude = position.coords.latitude;
          _this.longitude = position.coords.longitude;
        });
      }
    }
  }
}
</script>

<style scoped>
</style>
