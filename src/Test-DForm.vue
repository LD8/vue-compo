<template>
  <d-form class="form" ref="form" :model="user" :rules="rules">
    <d-form-item label="用户名" prop="username">
      <d-input v-model="user.username" placeholder="请输入用户名" />
    </d-form-item>

    <d-form-item label="密码" prop="password">
      <d-input v-model="user.password" placeholder="请输入密码" />
    </d-form-item>

    <d-button type="submit" @click="login">登 录</d-button>
  </d-form>
</template>

<script>
import DForm from "./form/DForm";
import DFormItem from "./form/DFormItem";
import DInput from "./form/DInput";
import DButton from "./form/DButton";

export default {
  name: "TestDForm",
  components: {
    DForm,
    DFormItem,
    DInput,
    DButton,
  },
  data() {
    return {
      user: {
        username: "",
        password: "",
      },
      rules: {
        username: [
          {
            required: true,
            message: "请输入用户名",
          },
        ],
        password: [
          {
            required: true,
            message: "请输入密码",
          },
          {
            min: 6,
            max: 12,
            message: "请输入6-12位密码",
          },
        ],
      },
    };
  },
  methods: {
    login(e) {
      this.$refs.form.validate((valid) => {
        if (valid) {
          alert("验证成功");
        } else {
          alert("验证失败");
          e.preventDefault();
        }
      });
    },
  },
};
</script>

<style>
.form {
  width: 30%;
  margin: 100px auto;
}
</style>