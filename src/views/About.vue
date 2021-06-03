<template>
<div>
  <div class="container">
    <div class="about">
      <h1>
      <word-scramble finalText="Hi" :delay="1500"></word-scramble>
      </h1>
      <p>
      <word-scramble finalText="I am Ehsan Jahanbakhsh. I love Web and I love being Simplistic. You can check out my work in /projects."
      :delay="1500" :speed="30" :scrambleChars="5"></word-scramble>
      </p>
    </div>
  </div>
    <div class="link-container">
      <router-link to="/"><word-scramble finalText="../" :delay="2000" hoverable></word-scramble></router-link>
      <router-link to="/projects"><word-scramble finalText="/projects" :delay="2000" hoverable></word-scramble></router-link>
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


.container {
  display: flex;
  justify-content: center;

}
.about {
  width: 100vmin;
  height: 20vh;
  font-size: 3vmin;
  overflow-wrap: anywhere;
  word-break:normal;
}

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
