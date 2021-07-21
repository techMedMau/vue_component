<template>
  <div id="app" class="container mx-auto">
    <div class="card" v-for="(item, index) in data" :key="index">
      <span v-if="index == 0"
        ><Card
          :src="data[index].src"
          :brand="data[index].brand"
          :feature="data[index].feature"
          :desc="data[index].desc"
          :isShow="isShow"
          :isBig="isBig"
      /></span>
      <span v-else>
        <Card
          :src="data[index].src"
          :brand="data[index].brand"
          :feature="data[index].feature"
          :desc="data[index].desc"
          :isShow="isShow"
      /></span>
    </div>
  </div>
</template>

<script>
import Card from "./components/Card";

export default {
  name: "App",
  components: {
    Card,
  },
  data() {
    return {
      data: [],
      isShow: true,
      isBig: true,
    };
  },
  created() {
    this.$http.get("../static/data.json").then((res) => {
      this.data = res.data;
    });
  },
};
</script>

<style lang="scss">
* {
  background-color: #eee;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  box-sizing: border-box;
}

.container {
  width: 1250px;
}
.mx-auto {
  margin-left: auto;
  margin-right: auto;
}

.card {
  height: max-content;
  margin: 15px;
  width: max-content;
  float: left;
}
</style>
