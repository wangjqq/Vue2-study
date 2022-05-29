<template>
  <div class="home-container">
    <h3>Home 组件</h3>

    <hr>

    <button @click="gotuMovie1">通过 push 跳转到电影1页面</button>
    <button @click="gotuMovie2">通过 replace 跳转到电影2页面</button>
    <button @click="goback">返回</button>
    <router-link to="/main">访问后台主页</router-link>
  </div>
</template>

<script>
export default {
  name: 'Home',
  methods: {
    gotuMovie1(){
      // 通过编程式导航 API,导航跳转到指定的页面
      this.$router.push('/movie/1')
    },
    gotuMovie2(){
      this.$router.replace('/movie/2')
    },
    goback(){
      // go(-1) 表示后退一层
      // 如果后退的层数超过上限,则原地不动
      this.$router.go(-1)
    }
  },
}
</script>

<style lang="less" scoped>
.home-container {
  min-height: 200px;
  background-color: pink;
  padding: 15px;
}
</style>
