<template>
  <div id="app">
   <biblio-list></biblio-list>
  </div>
</template>

<script>
import biblioList from "@/components/biblioList.vue";

export default {
  name: 'app',
  components: {
    biblioList
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
