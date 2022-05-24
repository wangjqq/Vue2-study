<template>
  <div
    class="number-container d-flex justify-content-center align-items-center"
  >
    <!-- 减 1 的按钮 -->
    <button type="button" class="btn btn-light btn-sm" @click="sub">-</button>
    <!-- 购买的数量 -->
    <span class="number-box">{{ count }}</span>
    <!-- 加 1 的按钮 -->
    <button type="button" class="btn btn-light btn-sm" @click="add">+</button>
  </div>
</template>

<script>
import bus from "@/components/eventBus.js";

export default {
  data() {
    return {};
  },
  methods: {
    sub() {
      if (this.count - 1 === 0) {
        return;
      }
      // 要发送给 App 的数据格式为{id,value}
      const obj = { id: this.id, value: this.count - 1 };
      // 通过 EventBus 把 obj 对象,发送给App组件
      bus.$emit("share", obj);
    },
    // 点击按钮数值+1
    add() {
      // 要发送给 App 的数据格式为{id,value}
      const obj = { id: this.id, value: this.count + 1 };
      // console.log(obj);
      // 通过 EventBus 把 obj 对象,发送给App组件
      bus.$emit("share", obj);
    },
  },
  props: {
    // 接收到的商品数量
    count: {
      default: 1,
      type: Number,
    },
    // 接收商品的id,使用 EventBus 方案
    // 把数量传递到 App.vue 的时候,需要通知 App 组件,更新哪个商品的数量
    id: {
      type: Number,
      required: true,
    },
  },
};
</script>

<style lang="less" scoped>
.number-box {
  min-width: 30px;
  text-align: center;
  margin: 0 5px;
  font-size: 12px;
}

.btn-sm {
  width: 30px;
}
</style>
