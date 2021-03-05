<template>
  <div>
    <h1>
      <span :class="{ winning: team1.score > team2.score }">{{
        team1.name
      }}</span
      >&nbsp; <span class="inlineP"><p>vs</p></span>&nbsp;
      <span :class="{ winning: team2.score > team1.score }"
        >{{ team2.name }}
      </span>
    </h1>
  </div>
</template>

<script>
export default {
  props: ["team1", "team2"],
};
</script>

<style scope>
h1 {
  text-align: center;
  font-size: 6vw;
  color: #fff;
}
p {
  font-size: 3vw;
  color: rgb(250, 110, 3);
}

.inlineP {
  display: inline-block;
}

.winning {
  color: yellow;
}
</style>