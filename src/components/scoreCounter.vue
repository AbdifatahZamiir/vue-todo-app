<template>
  <div class="hello text-center">
    <h1>{{ msg }}</h1>
    <div class="card">
      <div class="card-body">
        <h3>Player 1</h3>
        <button class="btn btn-success mr-3" @click="increaseCounter(player_1)">Up</button>
        <span>{{ player_1.score }}</span>
        <button class="btn btn-danger ml-3" @click="dencreaseCounter(player_1)">Down</button>
      </div>
      <div class="card-body">
        <h3>Player 2</h3>
        <button class="btn btn-success mr-3" @click="increaseCounter(player_2)">Up</button>
        <span>{{ player_2.score }}</span>
        <button class="btn btn-danger ml-3" @click="dencreaseCounter(player_2)">Down</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "scoreCounter",
  props: {
    msg: String,
    color: String
  },
  data() {
    return {
      player_1: {
        score: 0
      },
      player_2: {
        score: 0
      }
    };
  },
  methods: {
    increaseCounter(player) {
      player.score += 1;
    },
    dencreaseCounter(player) {
      if (player.score > 0) {
        player.score -= 1;
      }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.green {
  color: green;
}
</style>
