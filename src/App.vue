<template>
  <h1>Lucky Luke's Deadly Duel</h1>
  <Block v-if="isPlaying" :delay="delay" @gameOver="endGame" />
  <button
    id="luke"
    @mouseenter="mouseOnButton"
    @mouseleave="mouseOffButton"
    @click="start"
    :class="{ active: isActive }"
    :disabled="isPlaying"
  >
    Ready when you are!
  </button>
  <Results v-if="showResult" :score="score" />
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";

export default {
  name: "App",
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      isActive: false,
      delay: null,
      score: null,
      showResult: false,
    };
  },
  methods: {
    mouseOnButton() {
      this.isActive = true;
    },
    mouseOffButton() {
      this.isActive = false;
    },
    start() {
      (this.delay = 2000 + Math.random() * 5000),
        (this.isPlaying = true),
        (this.showResult = false);
    },
    endGame(reactionTime) {
      (this.score = reactionTime),
        (this.isPlaying = false),
        (this.showResult = true);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#luke {
  display: inline-flex;
  align-items: flex-end;
  justify-content: center;
  height: 400px;
  width: 400px;
  background-image: url("./assets/lucky_luke.png");
  background-size: cover;
  color: white;
  font-size: 2.5rem;
  text-shadow: 3px 3px 5px black;
}

.active {
  background-color: rgb(104, 102, 102);
}
</style>
