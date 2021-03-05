<template>
  <header>
    <p v-if="gameIsTied">The game is currently tied</p>
    <p v-else>{{ gameLeaderDisplay }}</p>
  </header>
</template>

<script>
export default {
  props: ["team1", "team2"],

  computed: {
    gameIsTied() {
      return this.$props.team1.score === this.$props.team2.score;
    },
    gameLeaderDisplay() {
      const { team1, team2 } = this.$props;
      const leadingTeam = team1.score > team2.score ? team1 : team2;
      const lead = Math.abs(team1.score - team2.score);
      const points = lead === 1 ? "point" : "points";

      return `${leadingTeam.name} is leading by ${lead} ${points}`;
    },
  },
};
</script>

<style scope>
header {
  align-content: center;
  text-align: center;
  justify-content: center;
  color: #fff;
  font-size: 2rem;
}
</style>