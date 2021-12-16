<template>
  <div class="disco">
      <img :src="dati.poster" alt="immagine">
      <h3 class="titolo">{{dati.title}}</h3>
      <span class="autore">{{dati.author}}</span>
      <span class="data">{{dati.year}}</span>
  </div>
</template>

<script>
export default {
    name: 'Dischi',
    props:{
        dati: Object
    }
}
</script>

<style lang="scss" scoped>

.disco{
    width: 200px;
    padding: 15px;
    background-color: #2e3a46;
    text-align: center;
    margin: 0 20px 20px 20px;

    img{
        width: 100%;
    }

    .titolo{
        color: white;
        font-size: 25px;
        padding: 10px 0 20px 0;
    }

    span{
        color: #7b7e79;
        font-size: 20px;
        font-weight: 500;
    }

    .autore{
        display: block;
    }
}

</style>