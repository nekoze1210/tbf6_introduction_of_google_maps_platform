<template>
  <div>
    <p id="result-view">{{ result }}</p>
  </div>
</template>

<script>
export default {
  props: ["map", "google", "result"],
  mounted() {
    let resultView = this.$el.querySelector("#result-view");
    this.map.controls[this.google.maps.ControlPosition.BOTTOM_CENTER].push(
      resultView
    );
  }
};
</script>

<style>
#result-view {
  width: 90%;
  min-height: 80px;
  font-size: 16px;
  background: #fff;
  margin-bottom: 20px;
  color: #333;
  border: 1px solid #ddd;
  border-radius: 3px;
}
</style>
