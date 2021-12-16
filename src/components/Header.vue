<template>
  <header>
      <Logo/>
  </header>
</template>

<script>
import Logo from './Logo.vue'

export default {
    name: 'Header',
    components:{
        Logo,
    }
}
</script>

<style lang="scss" scoped>

header{
    width: 100%;
    height: 90px;
    background-color: #2e3a46;
}

</style>