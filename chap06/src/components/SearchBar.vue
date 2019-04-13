<template>
  <div>
    <input
      id="search-bar"
      class="controls"
      type="text"
      placeholder="キーワード検索"
      v-model="keyword"
      @change="placeAutocomplete"
    >
  </div>
</template>

<script>
export default {
  props: ["map", "google"],
  data() {
    return {
      keyword: ""
    };
  },
  mounted() {
    // 検索窓の設置
    let searchBox = this.$el.querySelector("#search-bar");
    this.map.controls[this.google.maps.ControlPosition.TOP_CENTER].push(
      searchBox
    );
  },
  methods: {
    placeAutocomplete() {
      this.$emit("inputKeyword", this.keyword);
    }
  }
};
</script>

<style>
#search-bar {
  width: 80%;
  height: 40px;
  font-size: 16px;
  margin-top: 20px;
  border: 1px solid #ddd;
  border-radius: 3px;
}
</style>
