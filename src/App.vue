<template>
  <div id="app">
    <h1>Todo Application</h1>
    <hr>

    <router-view />
  </div>
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  max-width: 1600px;
  margin: 0 auto;
  padding-top: 60px;
  background: radial-gradient(circle, rgba(210,210,223,1) 0%, rgba(243,243,246,1) 50%, rgba(255,255,255,1) 100%, rgba(255,255,255,1) 100%);

  hr {
    margin: 50px 0;
    border: none;
    height: 2px;
    color: #b6b4d7;
    background-color: #b6b4d7;
  }
}
</style>
