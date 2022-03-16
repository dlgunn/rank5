<template>
  <nav-bar></nav-bar>
  <router-view />
  <footer-component></footer-component>
</template>

<script>
import NavBar from "@/components/NavBar.vue";
import FooterComponent from "@/components/FooterComponent.vue";
import mock from "./mock.js";

export default {
  components: {
    NavBar,
    FooterComponent,
  },
  data: function () {
    return {
      mock: mock,
      addedHistory: {},
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  padding: 0px;
  margin: 0px;
}
</style>
