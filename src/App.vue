<template>
  <div id="app"> 
    <game label=""/>
  </div>
</template>

<script>
import game from "./components/game.vue";
export default {
  name: "App",
  components: {
    game,
  },
};
</script>

<style>
body {
  background-image: url("https://images.alphacoders.com/963/thumb-1920-963492.png");
  background-size: 100% ;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: black;
  margin-top: 60px;
}
</style>
