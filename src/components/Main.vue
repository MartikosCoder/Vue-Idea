<template>
  <div class="main">
    <div class="latitude">Latitude: {{ latitude }}</div>
    <div class="longitude">Longitude: {{ longitude }}</div>
  </div>
</template>

<script>
export default {
  name: 'Main',
  data() {
    return {
      latitude: 0,
      longitude: 0
    }
  },
  created() {
    this.getCoords();
  },
  methods: {
    getCoords() {
      if (navigator.geolocation) {
        const _this = this;
        navigator.geolocation.getCurrentPosition(position => {
          _this.$set(_this, 'latitude', position.coords.latitude);
          _this.$set(_this, 'longitude', position.coords.longitude);
        });
      }
    }
  }
}
</script>

<style scoped>
</style>
