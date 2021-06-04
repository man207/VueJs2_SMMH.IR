<template>
  <div id="Home">
    <div class="subtitle">
      <h3>
        <word-scramble finalText="Front-End, Back-End Developer"
        :delay="1500" :speed="10" :scrambleChars="5"></word-scramble>
      </h3>
      <p>
        <word-scramble finalText="Innovative, Simplistic."
        :delay="1500" :speed="10" :scrambleChars="5"></word-scramble>
      </p>
    </div>
    <div class="link-container">
      <div class="link"> 
        <router-link to="/about"><word-scramble finalText="/aboutme" :delay="2000" hoverable></word-scramble></router-link>
      </div>
      <div class="link">
        <router-link to="/projects"><word-scramble finalText="/projects" :delay="2000" hoverable></word-scramble></router-link>
      </div>
      <div class="link">
        <router-link to="/challenges"><word-scramble finalText="/challenges" :delay="2000" hoverable></word-scramble></router-link>
      </div>
      <div class="link">
        <router-link to="/contact"><word-scramble finalText="/contact" :delay="2000" hoverable></word-scramble></router-link>
      </div>
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

.subtitle {
  margin-top: 20vh;
  text-align: center;
  margin-bottom: 20vh;
}

.link-container {
  font-size: 2vmax;
  display: flex;
  align-content: center;
  justify-content: space-around;
  flex-wrap: wrap;

}

.link {
    padding-bottom: 3ch;
}

@media (max-width: 728px) {

  .link {
    text-align: center;
    flex-basis: 100%;
  }
}


</style>
