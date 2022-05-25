<template>
  <div class="app-container">
    <h1>App 根组件</h1>
    <hr />
    <button @click="comName = 'Left'">展示 Left</button>
    <button @click="comName = 'Right'">展示 Right</button>

    <div class="box">
      <!-- 渲染 Left 组件和 Right 组件 -->
      <!-- 1.component 标签是 vue 内置的,作用:组件的占位符 -->
      <!-- 2.is 属性的值,表示要渲染的组件的名字 -->

      <!-- keep-alive 可以把内部的的组件进行缓存,而不是销毁组件 -->
      <!-- include 要缓存的组件,其他组件不会被缓存 -->
      <!-- exclude 不被缓存的组件,不要与include同时使用 -->
      <keep-alive exclude="MyRight">
        <component :is="comName"></component>
      </keep-alive>
    </div>
  </div>
</template>

<script>
import Left from "@/components/Left.vue";
import Right from "@/components/Right.vue";
export default {
  data() {
    return {
      // comName 表示要展示的组件的名称
      comName: "Left",
    };
  },
  components: {
    // 如果在声明组件的时候,没有为组件指定 name 名称,则组件的名称默认就是注册的名称
    Left,
    Right,
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
