<template>
  <div id="app">
    <UserInfo></UserInfo>

  </div>
</template>

<script>
import UserInfo from './components/UserInfo'

export default {
  name: 'App',
  components: {
    UserInfo
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
