<template>
  <div id="app">
    <nav-bar/>
    <main-box :dischi="dischi"/>
  </div>
</template>

<script>
import axios from 'axios'
import MainBox from './components/MainBox.vue'
import NavBar from './components/NavBar.vue'


export default {
  name: 'App',
  components: {
   NavBar,
    MainBox
  },

  data(){
    return{
      dischi : []
    }
  },
  mounted(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music').then((response) => {
      this.dischi = response.data.response
    })
  }
}
</script>

<style lang="scss">
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
}
</style>
