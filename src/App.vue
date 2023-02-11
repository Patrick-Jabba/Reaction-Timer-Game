<script setup>
import { reactive } from "vue";
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";

const state = reactive({
  isPlaying: false,
  delay: null,
  score: null,
  showResults: false
})
  function start() {
    state.showResults = false;
    state.delay = 2000 + Math.random() * 5000;
    state.isPlaying = true;
  }

  function endGame(reactionTime) {
    state.score = reactionTime;
    state.showResults = true;
    state.isPlaying = false;
  }
</script>

<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="start" :disabled="state.isPlaying">Play</button>
  <Block :delay="state.delay" v-if="state.isPlaying" @end="endGame" />
  <Results :results="state.score" v-if="state.showResults" />
</template>


<style>

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}

button {
  background: #03fcb3;
  border-radius: 4px;
  font-weight: bold;
  color: #444;
  width: 10%;
  height: 50px;
  font-size: 24px;
  border: 1px solid #444;
  cursor: pointer;
}

button:disabled {
  background-color: #ccc;
  color: #ddd;
  cursor: default;
}
</style>
