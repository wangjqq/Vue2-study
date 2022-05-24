<template>
  <div class="app-container">
    <!-- 头部区域 -->
    <Header></Header>
    <!-- 商品列表 -->
    <Goods
      v-for="item in list"
      :key="item.id"
      :title="item.goods_name"
      :picture="item.goods_img"
      :price="item.goods_price"
      :state="item.goods_state"
      :id="item.id"
      :count="item.goods_count"
      @state-change="getNewState"
    ></Goods>
    <!-- 底部区域 -->
    <Footer
      :stateAllTrue="stateAllTrue"
      :amount="amt"
      :totalCount="totalCount"
      @allState-change="allStateChange"
    ></Footer>
  </div>
</template>

<script>
// 导入axios
import axios from "axios";
// 导入需要的组件
import Header from "@/components/Header/Header.vue";
import Goods from "@/components/Goods/Goods.vue";
import Footer from "@/components/Footer/Footer.vue";

import bus from "@/components/eventBus.js";

export default {
  components: {
    Header,
    Goods,
    Footer,
  },
  methods: {
    // 封装请求列表数据的方法
    async initCartList() {
      const { data: res } = await axios.get("https://www.escook.cn/api/cart");
      this.list = res.list;
      // console.log(res);
    },
    // 接收子组件传递过来的数据
    // e 的格式为{id,value}
    getNewState(e) {
      this.list.some((item) => {
        if (item.id === e.id) {
          item.goods_state = e.value;
          return true;
        }
      });
    },
    // 接收 footer 传回的数据 是否全选
    allStateChange(e) {
      this.list.forEach((item) => (item.goods_state = e.value));
    },
  },
  // 组件创建的时候初始化列表
  created() {
    this.initCartList();
    bus.$on("share", (val) => {
      this.list.some((item) => {
        if (item.id === val.id) {
          item.goods_count = val.value;
          return true;
        }
      });
    });
  },
  data() {
    return {
      // 用来存储获取到的购物车列表,默认为空数组
      list: [],
    };
  },
  // 计算属性
  computed: {
    // 是否全选
    stateAllTrue() {
      return this.list.every((item) => item.goods_state);
    },
    //  已勾选商品的总价
    amt() {
      // 1.先 filter 过滤
      // 2.再 reduce 相加
      return this.list
        .filter((item) => item.goods_state)
        .reduce(
          (total, item) => (total += item.goods_price * item.goods_count),
          0
        );
    },
    // 已勾选商品的总数量
    totalCount() {
      // 先过滤再相加
      return this.list
        .filter((item) => item.goods_state)
        .reduce((total, item) => (total += item.goods_count), 0); //初始值是0 会累加
    },
  },
};
</script>

<style lang="less" scoped>
.app-container {
  padding-top: 45px;
  padding-bottom: 50px;
}
</style>
