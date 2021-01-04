<template>
  <d-form class="form" ref="form" :model="user" :rules="rules">
    <d-form-item label="用户名" prop="username">
      <d-input
        :value="user.username"
        @input="user.username = $event"
        placeholder="请输入用户名"
      />
    </d-form-item>

    <d-form-item label="密码" prop="password">
      <d-input
        :value="user.password"
        v-model="user.password"
        placeholder="请输入密码"
      />
    </d-form-item>

    <d-form-item>
      <d-button type="primary" @click.prevent="login">登录</d-button>
    </d-form-item>
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
    login() {
      console.log("submitting");
    },
  },
};
</script>

<style>
.form {
  width: 30%;
  margin: 150px auto;
}
</style>