<template>
  <div id="app">
    <div class="background-top"></div>
    <div class="app-indicator"></div>
    <v-main-container />
    <!-- <div class="bottom-wrp">
      <div class="home-indicator"></div>
    </div> -->
  </div>
</template>

<script>
  import vMainContainer from './components/v-main-container'

  export default {
    name: 'App',
    components: {
      vMainContainer
    }
  }
</script>

<style lang="scss">
  #app {
    width: 100vw;
    height: 100vh;
    background: #7D7C7F;
    display: flex;
    flex-direction: column;
    // font-family: Avenir, Helvetica, Arial, sans-serif;
    // -webkit-font-smoothing: antialiased;
    // -moz-osx-font-smoothing: grayscale;
  }
</style>
