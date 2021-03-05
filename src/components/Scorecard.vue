<template>
  <div class="box">
    <div class="scoreCard">
      <h2>{{ score }}</h2>
      <button class="decrement" @click="subtractPoint">-</button>
      <button class="increment" @click="addPoint">+</button>
    </div>
  </div>
</template>

<script>
export default {
  props: ["score"],

  methods: {
    addPoint() {
      this.$emit("pointAdded");
    },
    subtractPoint() {
      this.$emit("pointSubtracted");
    },
  },
};
</script>

<style>
</style>