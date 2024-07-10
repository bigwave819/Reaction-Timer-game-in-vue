<template> 
<h1>
  Wave Reaction Timer
</h1>

<button @click="start" :disabled="isPlaying">
  start
</button>
<Block v-if="isPlaying" :delay="delay" @end="endGame"/>
<Result v-if="showResult" :score="score"/>
</template>

<script>
import Block from './components/Block.vue'
import Result from './components/Result.vue'
export default {
  name: 'App',
  components : { Block, Result },
  data() {
    return{
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000,
      this.isPlaying = true
      this.showResult =false
    },
    endGame(reactionTime) {
      this.score = reactionTime,
      this.showResult= true,
      this.isPlaying = false
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
button{
  background: #06c99f;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled]{
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
