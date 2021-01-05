<template>
  <button v-bind="$attrs" v-on="$listeners"><slot /></button>
</template>

<script>
export default {
  name: "DButton",
  inheritAttrs: false,
};
</script>

<style>
</style>