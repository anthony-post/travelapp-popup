<template>
  <div id="app">
    <div class="app-indicator"></div>
      <v-main-container /> 
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
    max-width: 375px;
    padding-top: 90px;
    background: #7D7C7F;
    // font-family: Avenir, Helvetica, Arial, sans-serif;
    // -webkit-font-smoothing: antialiased;
    // -moz-osx-font-smoothing: grayscale;
  }
</style>
