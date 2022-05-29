<template>
  <div class="movie-container">
    <!-- this.$route 是路由的参数对象 -->
    <!-- this.$router 是路由的导航对象 -->
    <h3>Movie 组件 --- {{this.$route.params.id}} --- {{id}}</h3>
    <button @click="showThis">打印 this</button>
    <!-- 在行内使用编程式导航跳转, this 必须省略 -->
    <button @click="$router.back()">back 后退</button>
    <button @click="$router.forward()">forward 前进</button>
  </div>
</template>

<script>
export default {
  name: 'Movie',
  // 接收 props 数据
  props:['id'],
  methods:{
    showThis(){
      console.log(this);
    }
  }
}
</script>

<style lang="less" scoped>
.movie-container {
  min-height: 200px;
  background-color: lightsalmon;
  padding: 15px;
}
</style>
