<template>
  <div id="app">
    <div id="nav">
      <div :class="{'navbar': true, 'landing-text': isHome}">
        <console-text staticText="ejbb.me/" :dynamicText="dynamicText " :fromHome="isHome"></console-text>
    </div>
    </div>
    <div>
      <router-view/>
    </div>
  </div>
</template>


<script>
import ConsoleText from './components/ConsoleText.vue'
import Vue from 'vue';

export default {
  components: {
    ConsoleText,
  },
  computed: {
    isHome() {
      return this.$route.name == 'Home';
    },
    dynamicText() {
      return this.$route.path.slice(1) ;
    }
  },
  created() {
    Vue.prototype.$info = fetch("../public/info.json")
  }

}
</script>


<style lang="scss">
#app {
  font-family:monospace;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  padding: 0;
  margin: 0;
}

#nav {
  display: flex;
  justify-content: center;
  height: 20vh;
  font-size: 3vmax;
}


.navbar {
  transition: 1s;
  padding-top: 5vh;

}


.landing-text {
  padding-top: 10vh;

}



@media (max-width: 728px) {
  #nav {
    height: 15vh;
  }
  .navbar {
    transition: 1s;
    padding-top: 2vh;
  }
  .landing-text {
  padding-top: 10vh;

  }
}

</style>
