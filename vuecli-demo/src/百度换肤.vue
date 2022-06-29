<template>
  <div>
    <div class="imglist">
      <h3>图片列表区</h3>
      <img
        src="./assets/01.jpg"
        alt=""
        @mouseover="mouseover(1)"
        @click="click(1,$event)"
      />
      <img
        src="./assets/02.jpg"
        alt=""
        @mouseover="mouseover(2)"
        @click="click(2,$event)"
      />
      <img
        src="./assets/03.jpg"
        alt=""
        @mouseover="mouseover(3)"
        @click="click(3,$event)"
      />
    </div>
    <div class="show">
      <h3>图片预览区</h3>
      <img v-bind:src="img" alt="" style="width: 600px; height: auto" />
    </div>
  </div>
</template>
<script>
import img1 from "./assets/01.jpg";
import img2 from "./assets/02.jpg";
import img3 from "./assets/03.jpg";
export default {
  name: "App",
  data() {
    return {
      img: img1,
    };
  },
  methods: {
    mouseover(val) {
      this.img = { 1: img1, 2: img2, 3: img3 }[val];
    },
    click(val,e) {
      alert(`第${val}图片 地址：${e.target.src}`)
    },
  },
};
</script>
<style>
.container {
  display: flex;
}
.imglist {
  border: 2px solid red;
}
.imglist img {
  width: 200px;
  height: auto;
}
.show {
  border: 2px solid red;
  margin-right: 20px;
}
</style>
