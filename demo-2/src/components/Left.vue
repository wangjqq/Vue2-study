<template>
  <div class="left-container">
    <h3>Left 组件 --- {{ msgFromRight }}</h3>
    <p>msg:{{ msg }}</p>
    <p>user:{{ user }}</p>
    <button @click="msg = '123'">修改 msg</button>
    <button @click="user = { address: 'bj' }">修改 user</button>
    <hr />
    <div v-for="(item, id) in arr" :key="id">{{ item.name }}</div>
  </div>
</template>

<script>
import bus from "./eventBus";

export default {
  data() {
    return {
      msgFromRight: 0,
      arr: [
        { id: 1, name: "zs" },
        { id: 2, name: "ls" },
      ],
    };
  },
  created() {
    // 2.为 bus 绑定自定义事件
    bus.$on("share", (val) => {
      this.msgFromRight = val;
    });
  },
  props: ["msg", "user"],
};
</script>

<style lang="less">
.left-container {
  padding: 0 20px 20px;
  background-color: orange;
  min-height: 250px;
  flex: 1;
}
</style>
