<template>

    <div class="background">
        <div class="image">
            <img :src="disco.poster" alt="">
        </div>
        <h2>{{disco.title}}</h2>
        <span>{{disco.author}}</span>
        <h6>{{disco.year}}</h6>
    </div>

</template>

<script>
export default {
    props:{
        disco : Object
    }
}
</script>

<style lang="scss" scoped>

    .background{
      text-align: center;
      width: 240px;
      height: 400px;
      background-color: #2E3A46;
      margin: 10px 30px;
      padding: 20px 20px;
       img{
           width: 200px;
       }

       h2{
           color: #fff;
           font-size: 28px;
           margin: 8px 0;
       }

       span{
           color: #7C7A76;
           margin-bottom: 10px;
           font-size: 22px;
       }

       h6{
           color: #7C7A76;
           margin-top: 5px;
           font-size: 16px;
       }
    }

</style>