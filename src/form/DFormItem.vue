<template>
  <div>
    <label>{{ label }}</label>
    <div>
      <slot />
      <div v-for="em in errMessages" :key="em" class="danger">
        <p>{{ em }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import Schema from "async-validator";

export default {
  name: "DFormItem",
  inject: ["form"],
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
      errMessages: [],
    };
  },
  mounted() {
    // 注册 验证 事件
    this.$on("validate", () => {
      this.validate();
    });
  },
  methods: {
    validate() {
      const key = this.prop;
      const value = this.form.model[key];
      const rule = this.form.rules[key];

      const validator = new Schema({ [key]: rule });
      return validator.validate({ [key]: value }, (errors, fields) => {
        if (errors) {
          return this.handleErrors(errors, fields);
        }
        this.errMessages = [];
      });
    },

    handleErrors(errors, fields) {
      this.errMessages = errors.map((err) => err.message);
      console.log(fields);
    },
  },
};
</script>

<style>
.danger {
  color: red;
  font-size: 9px;
}
</style>