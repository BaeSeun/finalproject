<template>
  <div id="app">
    <navi-bar />
    <router-view />
  </div>
</template>

<script>
import NaviBar from "./components/layout/NaviBar.vue";

export default {
  name: "App",
  components: {
    NaviBar,
  },
};
</script>

<style>
/* html {
  background: url("./assets/Animal_Crossing.jpg") no-repeat 50% 50% fixed;
  -webkit-background-size: cover;
  -moz-background-size: cover;
  -o-background-size: cover;
  background-size: cover;
}*/

#app {
  /* background-image: url("./assets/Animal_Crossing.jpg");
  background-size: cover; */
  background-color: #62c15b;
}

a:hover {
  text-decoration: none;
  font-weight: bold;
}

a.router-link-exact-active {
  color: lightpink;
}
</style>
