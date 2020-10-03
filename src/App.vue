<template>
  <div align="center">
    <div id="app" class="bx">
      <h1 class="ti">The Anime</h1>
      <h5 class="ro">The center of anime and manga information around the world.</h5>
      <img alt="Vue logo" src="./assets/hl1.png" />
    </div>
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
.ti {
  color: rgb(251, 251, 247);
  font-size: 60px;
}
.ro{
  color: white;
}
.bx {
  background-color:rgba(48, 97, 201, 0.68);
  width: 900px;
  padding: 20px;
  margin: 25px;
}
</style>
