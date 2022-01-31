<template>
    <div class="container">
        <div class="container-dischi">
            <single-card v-for="(disco, index) in dischi" :key="index" :disco="disco"/>
        </div>
    </div>
</template>

<script>
import SingleCard from './SingleCard.vue'
export default {
   components: {
       SingleCard
   },
   props:{
       dischi : Array
   }
}
</script>

<style lang="scss" scoped>
 .container{
    height: 875px;
    background-color: #1E2D3B;
    display: flex;
    flex-wrap: wrap;

    .container-dischi{
    margin: 20px auto;
    width: 1500px;
    display: flex;
    flex-wrap: wrap;
    }
 }
</style>