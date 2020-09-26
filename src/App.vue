<template>
  <div id="app">
    <h1 class="ti" >The Movie</h1>
    <img alt="Vue logo" src="./assets/l2.png" />
    <anime />
  </div>
</template>

<script>
import Anime from "./components/Anime";
export default {
  name: "App",
  components: {
    Anime,
  },
};
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
.ti{
  color: rgb(251, 251, 247);
  font-size: 60px;
}
</style>
