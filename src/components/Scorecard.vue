<template>
  <div class="box">
    <div class="scoreCard">
      <p class="teamName">{{ team }}</p>
      <h2>{{ score }}</h2>
      <button class="closest" @click="addClosest">CLOSEST</button>
      <button class="ringer" @click="addRinger">RINGER</button>
      <button class="decrement" @click="subtractPoint">TAKE AWAY POINTS</button>
    </div>
  </div>
</template>

<script>
export default {
  props: ["team", "score"],

  methods: {
    addClosest() {
      this.$emit("closest");
    },
    addRinger() {
      this.$emit("ringer");
    },
    subtractPoint() {
      this.$emit("pointSubtracted");
    },
  },
};
</script>

<style scope>
.box {
  width: 100%;
  display: flex;
  justify-items: center;
  justify-content: center;
  text-align: center;
}

.scoreCard {
  text-align: center;
  border: 1rem #f4f4f4 solid;
  border-radius: 2px;
  width: 30vw;
  height: 40vw;
  /* margin: 2rem; */
  padding: 1rem;
}

h2 {
  font-size: 7vw;
  color: #fff;
  text-align: center;
  margin-bottom: 2rem;
}

/* p .teamName {
  text-align: center;
  font-size: 6vh;
} */

button {
  text-align: center;
  width: 14vw;
  font-size: 1vw;
  color: #fff;
  margin: 5px;
  padding: 0.5rem;
}

.decrement {
  background: rgb(255, 0, 0, 0.5);
  border: 2px rgb(255, 0, 0) solid;
  margin-top: 1rem;
}
.decrement:hover {
  background: rgb(255, 0, 0, 0.9);
}

.ringer,
.closest {
  background: rgba(1, 175, 1, 0.5);
  border: 2px rgb(0, 255, 0) solid;
}
.ringer:hover,
.closest:hover {
  background: rgb(1, 175, 0, 0.9);
}

/* .closest {
  background: rgba(76, 158, 129, 0.5);
  border: 2px rgb(0, 255, 0) solid;
}
.closest:hover {
  background: rgba(3, 120, 55, 0.9);
} */
</style>