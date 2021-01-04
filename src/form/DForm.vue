<template>
  <form>
    <slot />
  </form>
</template>

<script>
export default {
  name: "DForm",
  props: {
    model: {
      type: Object,
    },
    rules: {
      type: Object,
    },
  },
};
</script>

<style>
</style>