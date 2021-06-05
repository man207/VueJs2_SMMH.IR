<template>
<div id="About">
  <div class="container">
    <div class="about">
      <h1>
        <word-scramble finalText="Hi" :delay="1500"></word-scramble>
      </h1>
      <p class="me">
        <word-scramble finalText="I am Smmh. I love Web and I love being Simplistic... While Building Complex Systems"
        :delay="1500" :speed="20" :scrambleChars="5"></word-scramble>
      </p>
      <h2>
        <word-scramble finalText="My Skills:" :delay="4000"></word-scramble>
      </h2>
      <div class="skills">
        <div class="skillset">
          <h3>
           <word-scramble finalText="Front-End:" :delay="4000"></word-scramble>
          </h3>
        <ul>
        <li>
          <word-scramble finalText="HTML" :delay="4000"></word-scramble>
        </li>
        <li>
          <word-scramble finalText="CSS" :delay="4000"></word-scramble>
        </li>
        <li>
          <word-scramble finalText="JavaScript" :delay="4000"></word-scramble>
        </li>
        <li>
          <word-scramble finalText="VueJs" :delay="4000"></word-scramble>
        </li>
        </ul>
        </div>

        <div class="skillset">
          <h3>
           <word-scramble finalText="Back-End:" :delay="4000"></word-scramble>
          </h3>
        <ul>
        <li>
          <word-scramble finalText="NodeJs" :delay="4000"></word-scramble>
        </li>
        <li>
          <word-scramble finalText="Python" :delay="4000"></word-scramble>
        </li>
        <li>
          <word-scramble finalText="Django" :delay="4000"></word-scramble>
        </li>
        <li>
          <word-scramble finalText="ExpressJs" :delay="4000"></word-scramble>
        </li>
        <li>
          <word-scramble finalText="MongoDB" :delay="4000"></word-scramble>
        </li>
        </ul>
        </div>
      </div>
    </div>
  </div>
    <div class="link-container">
      <router-link to="/"><word-scramble finalText="../" :delay="4000" hoverable></word-scramble></router-link>
      <router-link to="/projects"><word-scramble finalText="/projects" :delay="4000" hoverable></word-scramble></router-link>
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
  flex-basis: 100%;
  display: flex;
  justify-content: center;
}
.about {
  width: 100vmin;
  font-size: 1rem;
  word-break:normal;
  overflow-wrap: anywhere;
}

.me {
  min-height: 10vh;
}
a {
  text-decoration: none;
}

.link-container {
  padding-top: 5vh;
  font-size: 2.5vmax;
  font-weight: 900;
  display: flex;
  align-content: center;
  justify-content: space-around;
}

li{
   list-style-type: none; 
}

.skills {
  display: flex;
  .skillset {
    flex-basis: 50%;
  }
}
</style>
