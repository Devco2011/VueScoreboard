<template>
  <div id="app">
    <matchup-title :team1="team1" :team2="team2"></matchup-title>
    <game-status :team1="team1" :team2="team2"></game-status>
    <div class="scores">
      <scorecard
        :team="team1.name"
        :score="team1.score"
        @pointAdded="updateTeamScore(team1, 1)"
        @pointSubtracted="updateTeamScore(team1, -1)"
      ></scorecard>
      <scorecard
        :team="team2.name"
        :score="team2.score"
        @pointAdded="updateTeamScore(team2, 1)"
        @pointSubtracted="updateTeamScore(team2, -1)"
      ></scorecard>
    </div>
  </div>
</template>

<script>
import Scorecard from "./components/Scorecard.vue";
import MatchupTitle from "./components/MatchupTitle.vue";
import GameStatus from "./components/GameStatus.vue";

export default {
  components: { MatchupTitle, Scorecard, GameStatus },

  data() {
    return {
      team1: {
        name: "Player 1",
        score: 0,
      },
      team2: {
        name: "Player 2",
        score: 0,
      },
    };
  },

  methods: {
    updateTeamScore(team, points) {
      const updated = team.score + points;

      if (updated >= 0) {
        team.score = updated;
      }
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Archivo+Black&display=swap");

body {
  background-color: #395e6b;
  font-family: "Archivo Black", sans-serif;
  color: rgb(250, 110, 3);
}
.scores {
  display: flex;
  justify-content: space-evenly;
}
</style>
