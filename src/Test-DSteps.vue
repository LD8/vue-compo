<template>
  <div>
    <d-steps :stepsCount="stepsCount" :currentStep="currentStep" />
    <button @click="previousStep">Prev Step</button>
    <button @click="nextStep">Next Step</button>
  </div>
</template>

<script>
import DSteps from "./steps/DSteps.vue";
export default {
  name: "TestDSteps",
  components: {
    DSteps,
  },
  data() {
    return {
      stepsCount: 5,
      currentStep: 1,
    };
  },
  methods: {
    nextStep() {
      if (this.currentStep < this.stepsCount) {
        this.currentStep++;
      }
    },
    previousStep() {
      if (this.currentStep > 1) {
        this.currentStep--;
      }
    },
  },
};
</script>

<style>
</style>