<template>
  <div>
    <input type="text" :value="val" @input="input" />
  </div>
</template>
<script>
export default {
  name: "App",
  data() {
    return {
      val: "",
    };
  },
  methods: {
    input(e) {
      this.val = e.target.value;
    },
  },
};
</script>
<style></style>
