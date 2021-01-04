<template>
  <div class="d-steps">
    <div class="d-steps-line"></div>
    <div
      class="d-step"
      v-for="stepNumber in stepsCount"
      :key="stepNumber"
      :style="{
        color:
          stepNumber === currentStep
            ? activeColor
            : stepNumber < currentStep
            ? doneColor
            : toDoColor,
      }"
    >
      {{ stepNumber }}
    </div>
  </div>
</template>

<script>
export default {
  name: "DSteps",
  props: {
    stepsCount: {
      type: Number,
      default: 3,
    },
    currentStep: {
      type: Number,
      default: 1,
    },
    activeColor: {
      type: String,
      default: "green",
    },
    doneColor: {
      type: String,
      default: "silver",
    },
    toDoColor: {
      type: String,
      default: "darkblue",
    },
  },
};
</script>

<style>
.d-steps {
  position: relative;
  display: flex;
  justify-content: space-between;
}

.d-steps-line {
  position: absolute;
  height: 2px;
  top: 50%;
  left: 24px;
  right: 24px;
  transform: translateY(-50%);
  z-index: 1;
  background: rgb(223, 231, 239);
}

.d-step {
  border: 2px solid;
  border-radius: 50%;
  height: 32px;
  width: 32px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-weight: 700;
  z-index: 2;
  background-color: white;
  box-sizing: border-box;
}
</style>