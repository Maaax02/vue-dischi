<template>
    <div>
        <select name="" id="">
            <option v-for="disco in dischi" :key="disco.value">{{disco.genre}}</option> 
        </select>
    </div>
</template>

<script>
export default {
    props:{
       dischi:Array
    }
}
</script>

<style lang="scss" scoped>

</style>