<template>
  <div></div>
</template>

<script>
export default {
  props: ["map", "position", "google"],
  mounted() {
    this.marker = new this.google.maps.Marker({
      position: this.position,
      map: this.map,
      draggable: true
    });
    this.google.maps.event.addListener(
      this.marker,
      "dragend",
      this.reverseGeocoding
    );
  },
  methods: {
    reverseGeocoding() {
      const lat = this.marker.getPosition().lat();
      const lng = this.marker.getPosition().lng();
      const latlng = lat + "," + lng;
      this.$emit("markerDragEnd", latlng);
    }
  }
};
</script>
