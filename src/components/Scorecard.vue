<template>
  <div class="box">
    <div class="scoreCard">
      <p class="teamName">{{ team }}</p>
      <h2>{{ score }}</h2>
      <button class="decrement" @click="subtractPoint">-</button>
      <button class="increment" @click="addPoint">+</button>
    </div>
  </div>
</template>

<script>
export default {
  props: ["team", "score"],

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

<style scope>
.box {
  width: 100vw;
  display: flex;
  justify-items: center;
  justify-content: center;
  text-align: center;
}

.scoreCard {
  border: 1rem #f4f4f4 solid;
  width: 20vw;
  height: 40vw;
  font-size: 6vw;
  margin: 2rem;
  padding: 3rem;
}

button {
  text-align: center;
  width: 6vw;
  font-size: 4vw;
  color: #fff;
  margin: 3px;
}

.decrement {
  background: rgb(255, 0, 0, 0.5);
  border: 2px rgb(255, 0, 0) solid;
}

.increment {
  background: rgb(0, 255, 0, 0.5);
  border: 2px rgb(0, 255, 0) solid;
}
</style>