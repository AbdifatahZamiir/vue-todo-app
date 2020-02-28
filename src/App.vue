<template>
  <div id="app" class="text-center">
    <scoreCounter :msg="msg" />
  </div>
</template>

<script>
import ScoreCounter from "./components/scoreCounter.vue";

export default {
  name: "App",
  components: {
    ScoreCounter
  },
  data() {
    return {
      msg: "Player Score"
    };
  }
};
</script>

<style scoped>
#app {
  color: blue;
}
</style>
