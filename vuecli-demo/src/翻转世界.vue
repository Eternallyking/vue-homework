<template>
  <div>
    <h1>{{ message }}</h1>
    <button @click="click">翻转</button>
  </div>
</template>
<script>
export default {
  name: "App",
  data() {
    return {
      message: "Hello,World!",
    };
  },
  methods: {
    click() {
      this.message = this.message.split("").reverse().join("");
    },
  },
};
</script>
<style>
</style>
