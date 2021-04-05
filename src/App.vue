<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <PasswordChecker/>
  </div>
</template>

<script>
import PasswordChecker from './components/PasswordChecker.vue'

export default {
  name: 'App',
  components: {
    PasswordChecker
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
