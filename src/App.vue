<template>
    <div id="app">
      <div class="header">
        <img class="logo" src="./assets/logo.png">
        <img class="test" src="./assets/test.png">
        <h2>Welcome to Your Vue.js App</h2>
      </div>
      <router-view></router-view>
    </div>
</template>

<script>
export default {
  name: 'app',
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  overflow-y: hidden;
}

.header{
  background: #eee;
  padding: 6rem 0;
}

.logo{
  position: relative;
  left: 1.5rem;
}

.test{
  position: relative;
  top: -9.7rem;
  left: -.5rem;
  height: 5rem;
}

</style>
