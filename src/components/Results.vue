<template>
  <div class="results">
    <h2>Tardaste: {{ score }} ms</h2>
    <p class="rank">{{ rank }}</p>
  </div>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 320) {
      this.rank = "El revolver más rápido del oeste";
    } else if (this.score < 400) {
      this.rank = "Rápido, pero no el más rápido";
    } else {
      this.rank = "Luke dice: bang bang estás liquidado";
    }
  },
};
</script>

<style>
.results {
  width: 400px;
  border-radius: 20px;
  background: lightgray;
  color: darkolivegreen;
  text-align-last: center;
  padding: 1em;
  margin: 1em auto;
}

.rank {
  color: darkgreen;
}
</style>
