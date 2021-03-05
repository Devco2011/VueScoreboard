<template>
  <div id="app">
    <p class="scoreboardTitle">Horseshoes Scoreboard</p>
    <matchup-title :team1="team1" :team2="team2"></matchup-title>
    <game-status :team1="team1" :team2="team2"></game-status>
    <div class="scores">
      <scorecard
        :team="team1.name"
        :score="team1.score"
        @closest="updateTeamScore(team1, 1)"
        @ringer="updateTeamScore(team1, 3)"
        @pointSubtracted="updateTeamScore(team1, -1)"
      ></scorecard>
      <scorecard
        :team="team2.name"
        :score="team2.score"
        @closest="updateTeamScore(team2, 1)"
        @ringer="updateTeamScore(team2, 3)"
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

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.container {
  background: rgba(4, 17, 114, 0.85);
  height: 100vh;
  position: relative;
}

.container:before {
  content: "";
  background: url("./assets/horseshoes2.jpg") no-repeat center center/cover;
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: -1;
}
body {
  font-family: "Archivo Black", sans-serif;
  color: rgb(250, 110, 3);
}
.scoreboardTitle {
  padding-top: 3rem;
  font-size: 2vh;
  text-align: center;
}

.scores {
  display: flex;
  justify-content: space-evenly;
}
</style>
