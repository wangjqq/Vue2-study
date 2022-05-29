<template>
  <div class="app-container">
    <h1>App2 组件</h1>

<!-- 当安装和配置了 vue-router 后,就可以使用 router-link 来替代普通的 a 链接 -->
  <!-- <a href="#/home">首页</a> -->
  <router-link to="/home">首页</router-link>
  <!-- 注意1:在 hash 地址中,/后面的参数项,叫做路径参数 -->
  <!-- 在路由参数对象中($route),需要使用this.$route.params来访问路径参数 -->

  <!-- 注意2:在 hash 地址中,?后面的参数项,叫做查询参数 -->
  <!-- 在路由参数对象中,需要使用 this.$route.query 来访问查询参数 -->
  
  <!-- 注意3:在 this.$route 中,path 只是路径部分,full Path 是完整的地址 -->
  <!-- 例如 -->
  <!-- /movie/2?name=zs&age=20 是 fullPath 的值 -->
  <!-- /movie/2 是 path 的值 -->
  <router-link to="/movie/1">电影1</router-link>
  <router-link to="/movie/2?name=zs&age=20">电影2</router-link>
  <router-link to="/movie/3">电影3</router-link>
  <router-link to="/about">关于</router-link>



    <hr />

    <!-- 只要在项目中安装和配置了 vue-router,就可以使用 router-view 这个组件 -->
    <!-- 它的作用很单纯:占位符 -->
    <router-view>

    </router-view>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style lang="less" scoped>
.app-container {
  background-color: #efefef;
  overflow: hidden;
  margin: 10px;
  padding: 15px;
  > a {
    margin-right: 10px;
  }
}
</style>
