<template>
  <div id="app">
    <matchup-title :team1="team1" :team2="team2"></matchup-title>
    <game-status :team1="team1" :team2="team2"></game-status>
    <div class="box">
      <scorecard
        :score="team1.score"
        @pointAdded="updateTeamScore(team1, 1)"
        @pointSubtracted="updateTeamScore(team1, -1)"
      ></scorecard>
      <scorecard
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
body {
  background-color: #03b8fa;
}
h1 {
  text-align: center;
  font-size: 5rem;
}

.box {
  display: flex;
  flex-wrap: wrap;
  justify-items: center;
  justify-content: center;
  text-align: center;
}

.scoreCard {
  border: 2px #f4f4f4 solid;
  font-size: 4rem;
  margin: 3rem;
  padding: 1rem;
}

button {
  width: 10vw;
  height: 10vh;
  font-size: 3rem;
  color: #fff;
  margin: 2rem;
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
