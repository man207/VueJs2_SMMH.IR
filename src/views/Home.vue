<template>
  <div id="app">
    <div class="link-container">
      <router-link to="/about"><word-scramble finalText="/aboutme" :delay="2000" hoverable></word-scramble></router-link>
      <router-link to="/projects"><word-scramble finalText="/projects" :delay="2000" hoverable></word-scramble></router-link>
      <router-link to="/contact"><word-scramble finalText="/contact" :delay="2000" hoverable></word-scramble></router-link>
    </div>
  </div>
</template>

<script>
import WordScramble from '../components/WordScramble.vue'

export default {
  name: 'App',
  components: {
    WordScramble
  }
}
</script>

<style lang="scss" scoped>
a {
  text-decoration: none;
}

.link-container {
  padding-top: 20vh;
  font-size: 3vw;
  display: flex;
  align-content: center;
  justify-content: space-around;
}

</style>
