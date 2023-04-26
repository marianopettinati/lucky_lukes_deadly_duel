<template>
  <div class="backdrop">
    <div class="block" v-if="showBlock" @click="stopTimer">Shoot!</div>
  </div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  updated() {},
  unmounted() {},
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("gameOver", this.reactionTime);
    },
  },
};
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  background: rgb(235, 234, 234);
  color: darkred;
  border: darkred solid 3px;
  font-size: 4rem;
  text-shadow: 3px 3px 15px red;
  text-align-last: center;
  padding: 80px;
  margin: 80px auto;
  cursor: pointer;
}

.backdrop {
  color: red;
  text-shadow: 2px 2px 20px white;
  padding: 10px;
  top: 0;
  position: fixed;
  background: rgba(0, 0, 0, 0.9);
  width: 100%;
  height: 100%;
  justify-content: center;
  font-size: 2em;
  cursor: not-allowed;
}
</style>
