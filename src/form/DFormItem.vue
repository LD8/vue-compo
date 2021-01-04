<template>
  <div>
    <label>{{ label }}</label>
    <div>
      <slot />
      <p>{{ errMessage }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "DFormItem",
  props: {
    label: {
      type: String,
    },
    // 需要验证的表单value名称
    prop: {
      type: String,
    },
  },
  data() {
    return {
      errMessage: "",
    };
  },
};
</script>

<style>
</style>