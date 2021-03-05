<template>
  <div>
    <h1>
      <span :class="{ winning: team1.score > team2.score }">{{
        team1.name
      }}</span>
      vs
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

<style>
.winning {
  color: yellow;
}
</style>