<template>
  <div>
    <input v-bind="$attrs" :type="type" :value="value" @input="handleInput" >
  </div>
</template>

<script>
export default {
  name: "DInput",
  // $attrs 工作的前提
  inheritAttrs: false,
  props: {
    value: {
      type: String,
    },
    type: {
      type: String,
      default: "text",
    },
  },
  methods: {
    handleInput(e) {
      this.$emit("input", e.target.value);
      // 找是 form-item 的父元素节点
      const findParent = (parent) => {
        while (parent) {
          if (parent.$options.name === "DFormItem") {
            break;
          } else {
            parent = parent.$parent;
          }
        }
        return parent;
      };
      const parent = findParent(this.$parent);
      if (parent) {
        // 触发 验证 事件
        parent.$emit("validate");
      }
    },
  },
};
</script>

<style>
</style>