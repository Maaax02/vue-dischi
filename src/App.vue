<template>
  <div id="app">
    <nav-bar :disco="dischi" />
    <select-genres @search="filterDisc" :dischi="dischi" :genere="notDuplicatedGenre"/>
    <main-box v-if="apiLoader" :dischi="genres" />
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
      genres:[]
    };
  },

computed:{

  notDuplicatedGenre(){
    let genere = [];
    this.dischi.forEach((element) => {
      if(!genere.includes(element.genre.toLowerCase())){
        genere.push(element.genre.toLowerCase())
      }
    })
    return genere;
  },
},

  methods:{
   

    filterDisc(genre){
      this.genres = this.dischi.filter((disc) => {
        return disc.genre.toLowerCase() === genre || genre === 'all';
      })
    }
  },
  
  mounted() {
    setTimeout(() => {
      axios
        .get("https://flynn.boolean.careers/exercises/api/array/music")
        .then((response) => {
          this.dischi = response.data.response;
          this.apiLoader = true;   
          this.genres = response.data.response;      
        });
    }, 1000);
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
 #app{
   background-color: #18D860;
 }
</style>
