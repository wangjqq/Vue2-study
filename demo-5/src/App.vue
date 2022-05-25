<template>
  <div class="app-container">
    <h1>App 根组件</h1>
    <hr />
    <Article>
      <template #title="scope">
        {{ scope }}
        <h3>一首诗</h3>
      </template>
      <template #content="{ msg }">
        <div>
          {{ msg }}
          <p>啊,大海,全是水</p>
          <p>啊,大海,全是水</p>
          <p>啊,大海,全是水</p>
        </div>
      </template>
      <template #author>
        <div>作者:王景奇</div>
      </template>
    </Article>
    <div class="box" style="display: none">
      <!-- 渲染 Left 组件和 Right 组件 -->
      <Left>
        <!-- 默认情况下,在使用组件的时候,提供的内容都会被填充到名字为 default 的插槽中 -->
        <!-- 1.如果要把内容填充到指定名称的插槽中,需要使用 v-slot:这个指令 -->
        <!-- 2.v-slot:后面要跟上插槽的名字 -->
        <!-- 3.v-slot:指令不能直接用在元素身上,必须用在 template 标签上 -->
        <!-- 4.template 这个标签,它是一个虚拟的标签,只起到包裹性质的作用,但是不会被渲染为任何实质性的 html 元素 -->
        <template #default>
          <!-- <p>这是在Left组件的内容区域,声明的p标签</p> -->
        </template>
      </Left>
    </div>
  </div>
</template>

<script>
import Left from "@/components/Left.vue";
import Article from "@/components/Article.vue";
export default {
  components: {
    Left,
    Article,
  },
};
</script>

<style lang="less">
.app-container {
  padding: 1px 20px 20px;
  background-color: #efefef;
}
.box {
  display: flex;
}
</style>
