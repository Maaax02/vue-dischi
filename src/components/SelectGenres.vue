<template>
    <div class="container">
        <select v-model="select" @change="$emit('search', select)">
            <option value="all">All</option>
            <option v-for="(item, index) in genere" :key="index" :value="item">{{item}}</option> 
        </select>
      
    </div>
</template>

<script>

export default {
    props:{
       dischi:Array,
       genere: Array
    },
    data(){
        return{
            select: 'All',
        }
    }
}
</script>

<style lang="scss" scoped>
.container{
    margin: 20px auto;
    width: 100px;
}
</style>