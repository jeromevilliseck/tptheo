<template>
  <div id="app">
   <biblio-list></biblio-list> <!--Le component bibliolist à été construit dans la classe biblioList.vue-->
  </div>
</template>

<script>
import biblioList from "@/components/biblioList.vue"; //On importe le component biblioList que l'on a construit
                                                        //Le @ reprend le chemin à partir du dossier src
export default {
  name: 'app', //Le nom à l'export du component App principal qui sera utilisé en Js avec #app
  components: {
    biblioList //Le component App est composé lui meme du component biblioList
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
