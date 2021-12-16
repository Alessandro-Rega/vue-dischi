<template>
  <main>
      <div class="container">
        <Dischi v-for="(disco, index) in arrayDischi" :key="index" :dati="disco"/>
      </div>
  </main>
</template>

<script>
import axios from 'axios';
import Dischi from './dischi/Dischi.vue'

export default {
    name: 'Main',
    components:{
        Dischi
    },
    data(){
        return {
            arrayDischi: null
        }
    },
    created(){
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
        .then((response) => {
            // handle success
            this.arrayDischi = response.data.response;
            console.log(this.arrayDischi);
        })
        .catch(function (error) {
            // handle error
            console.log(error);
        });
    }
}
</script>

<style lang="scss" scoped>

main{
    width: 100%;
    height: calc(100vh - 90px);
    background-color: #1e2d3b;
    padding-top: 50px;

    .container{
        width: 70%;
        margin: 0 auto;
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
    }
}

</style>