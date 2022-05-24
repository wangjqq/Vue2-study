<template>
  <div class="footer-container">
    <!-- 左侧的全选 -->
    <div class="custom-control custom-checkbox">
      <input
        type="checkbox"
        class="custom-control-input"
        id="cbFull"
        :checked="stateAllTrue"
        @change="stateChange"
      />
      <label class="custom-control-label" for="cbFull">全选</label>
    </div>

    <!-- 中间的合计 -->
    <div>
      <span>合计：</span>
      <span class="total-price">￥{{ amount.toFixed() }}</span>
    </div>

    <!-- 结算按钮 -->
    <button type="button" class="btn btn-primary btn-settle">
      结算（{{ totalCount }}）
    </button>
  </div>
</template>

<script>
export default {
  props: {
    // 是否全选
    stateAllTrue: {
      default: false,
      type: Boolean,
    },
    // 总价格
    amount: {
      type: Number,
      default: 0,
    },
    // 总数量
    totalCount: {
      type: Number,
      default: 0,
    },
  },
  methods: {
    // 全选框点击变化处理
    stateChange(e) {
      const newState = e.target.checked;
      this.$emit("allState-change", { value: newState });
    },
  },
};
</script>

<style lang="less" scoped>
.footer-container {
  font-size: 12px;
  height: 50px;
  width: 100%;
  border-top: 1px solid #efefef;
  position: fixed;
  bottom: 0;
  background-color: #fff;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 10px;
}

.custom-checkbox {
  display: flex;
  align-items: center;
}

#cbFull {
  margin-right: 5px;
}

.btn-settle {
  height: 80%;
  min-width: 110px;
  border-radius: 25px;
  font-size: 12px;
}

.total-price {
  font-weight: bold;
  font-size: 14px;
  color: red;
}
</style>
