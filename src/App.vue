<template>  
  <div id="app">
    <br/>
    <img class="rounded-circle" src="" width="20%" />
    
    <br/>
    <h1 class="text-light container">❰❰❰❰❰❰❰❰❰❰❰❰❰❰❰❰❰❰❰❰❰ 〔 WAR IS ON 〕 ❱❱❱❱❱❱❱❱❱❱❱❱❱❱❱❱❱❱❱❱❱❱</h1><br>
    <div>
      <botton />
    </div>  
    <!-- <img src=""> -->
    <!-- <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to The infinity war game"/> -->
    <game/>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import game from './components/game.vue'

export default {
  name: 'App',
  components: {
    // HelloWorld,
    game,
  },
};
</script>

<style>
#app {    
  background-image: url(https://wallpaperhd.wiki/wp-content/uploads/space-background-2560x1440-space-background-2560x1440-moon-rays-red-space-sky-abstract-mountains.jpg) ;
  background-attachment: fixed;
  background-repeat: no-repeat;
  background-size: 100% ;
  height: 100vh;
  text-align: center;
  font-family: 'Mitr', sans-serif;
  position: relative;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #000000;
}
</style>
