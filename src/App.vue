<template>
  <div id="app">
    <div class="landing-text">
      <console-text finalText="SMMH.IR" ></console-text>
    </div>
    <div class="link-container">
      <word-scramble finalText="/aboutme" :delay="2000"></word-scramble>
      <word-scramble finalText="/projects" :delay="2000"></word-scramble>
      <word-scramble finalText="/contact" :delay="2000"></word-scramble>
    </div>
  </div>
</template>

<script>
import ConsoleText from './components/ConsoleText.vue'
import WordScramble from './components/WordScramble.vue'

export default {
  name: 'App',
  components: {
    ConsoleText,
    WordScramble
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.landing-text {
  padding-top: 20vh;
}

.link-container {
  display: flex;
  align-content: center;
  justify-content: space-around;
}

</style>
