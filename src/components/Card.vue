<template>
  <div v-on:mouseenter="show = !show" v-on:mouseleave="show = !show">
    <div class="img_inner" :class="{ big: big }">
      <img
        class="img_resp"
        :class="{ zoom: !show }"
        :src="src"
        :alt="brand"
        width="500"
        height="500"
      />
      <div class="text">
        <h3 class="title m_reset" :class="{ orange: !show }">{{ brand }}</h3>
        <p class="feature m_reset">{{ feature }}</p>
        <p :class="{ none: show }" class="feature m_reset hide">{{ desc }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: ["src", "brand", "feature", "desc", "isShow", "isBig"],
  data() {
    return {
      show: this.isShow,
      big: this.isBig,
    };
  },
};
</script>

<style scoped>
.img_inner {
  width: 278px;
  height: 278px;
  position: relative;
  clear: both;
  overflow: hidden;
}

.img_resp {
  width: 100%;
  height: 100%;
}

.zoom {
  transform: scale(1.2);
}

.title {
  color: #ccc;
  font-style: italic;
  background-color: transparent;
}

.feature {
  color: #fff;
  background-color: transparent;
}

.text {
  position: absolute;
  bottom: 0;
  text-align: left;
  width: 100%;
  padding-top: 30px;
  background: linear-gradient(transparent, rgb(54, 54, 54));
}

.m_reset {
  margin: 0.5rem;
}

.none {
  display: none;
}

.orange {
  color: #f2a93b;
}

.hide {
  margin-bottom: 1rem;
  font-size: 15px;
}

.big {
  width: 585px;
  height: 585px;
  float: left;
}
</style>
