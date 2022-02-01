<template>
  <div id="app">
    <nav-bar :disco="dischi" />
    <select-genres :dischi="dischi"/>
    <main-box v-if="apiLoader" :dischi="dischi" />
    <loader v-else />
  </div>
</template>

<script>
import axios from "axios";
import MainBox from "./components/MainBox.vue";
import SelectGenres from "./components/SelectGenres.vue";
import NavBar from "./components/NavBar.vue";
import Loader from "./components/Loader.vue";



export default {
  name: "App",
  components: {
    NavBar,
    MainBox,
    Loader,
    SelectGenres
  },

  data() {
    return {
      dischi: [],
      apiLoader: false,
    };
  },
  
  mounted() {
    setTimeout(() => {
      axios
        .get("https://flynn.boolean.careers/exercises/api/array/music")
        .then((response) => {
          this.dischi = response.data.response;
          this.apiLoader = true;
        });
    }, 100);
  },
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
    "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
}
</style>
