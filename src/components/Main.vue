<template>
  <main>
      <div class="selezione">
        <select name="genere" id="genere" v-model="searchDisco" @change="cercaDischi">
            <option value="">All</option>
            <option value="rock">Rock</option>
            <option value="pop">Pop</option>
            <option value="jazz">Jazz</option>
            <option value="metal">Metal</option>
        </select>
      </div>
      <div class="container" v-if="arrayDischi != null">
        <Dischi v-for="(disco, index) in dischiFiltro" :key="index" :dati="disco"/>
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
            arrayDischi: null,
            searchDisco: ""
        }
    },
    created(){
        axios.get('https://flynn.boolean.careers/exercises/api/array/music')
        .then((response) => {
            // handle success
            this.arrayDischi = response.data.response;
        })
        .catch(function (error) {
            // handle error
            console.log(error);
        });
    },
    methods: {
        cercaDischi() {
            // this.searchDisco = this.searchDisco;
        }
    },
    computed:{
        dischiFiltro() {
            console.log(this.searchDisco);
            const arrayDischiFiltrato = this.arrayDischi.filter( (elm) => {
                return elm.genre.toLowerCase().includes(this.searchDisco.toLowerCase()); // true o false
            });
            return arrayDischiFiltrato;
        }
    }
}
</script>

<style lang="scss" scoped>

main{
    width: 100%;
    height: calc(100vh - 90px);
    background-color: #1e2d3b;

    .selezione{
        width: 70%;
        height: 50px;
        margin: 0 auto;
        margin-bottom: 20px;
        text-align: left;
        line-height: 45px;

        #genere{
            padding: 5px 20px;
            margin-left: 20px;
        }
    }

    .container{
        width: 70%;
        margin: 0 auto;
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
    }
}

</style>