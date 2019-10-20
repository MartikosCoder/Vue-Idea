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
      longitude: 0,
      watchCoords: null
    }
  },
  created() {
    this.getCoords();
  },
  beforeDestroy() {
	   clearInterval(this.watchCoords);
  },
  methods: {
    getCoords() {
      if (navigator.geolocation) {
        const _this = this;
        _this.watchCoords = setInterval(() => {
          navigator.geolocation.getCurrentPosition(position => {
            _this.$set(_this, 'latitude', position.coords.latitude.toFixed(2));
            _this.$set(_this, 'longitude', position.coords.latitude.toFixed(2));
          });
        }, 1000);
      }
    }
  }
}
</script>

<style scoped>
</style>
