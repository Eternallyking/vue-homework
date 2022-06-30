<template>
  <div id="app">
    <ul>
      <li v-for="item in myArr" :key="item">{{item}}</li>
    </ul>
    <button @click="click">走一走</button>
  </div>
</template>

<script>

export default {
  name: 'App',
  data () {
    return {
      myArr: ["帅哥", "美女", "程序猿"],
    }
  },
  methods: {
    click(){
      this.myArr.push(this.myArr[0])
      this.myArr.splice(0, 1)
    }
  }
}
</script>

<style>

</style>
