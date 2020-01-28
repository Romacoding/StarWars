<template>
  <div id="app">
    <img alt="Star Wars logo" src="./assets/star-wars.svg" />
    <StarWars msg="May the Force be with you" />
  </div>
</template>

<script>
import StarWars from "./components/StarWars.vue";

export default {
  name: "app",
  components: {
    StarWars
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
img {
  width: 150px;
}
</style>
