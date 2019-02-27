<template>
    <span>RCR : {{ rcr }}, NOM : {{ nom }}</span>
    <!--Les props seront utilisées dynamiquent dans le composant père en étant déclaré en attribut
    :nom_props="valeur absolue"
    ou :nom_props=fonction()
    ou :nom_props=-->
</template>

<script>
    export default {
        name: "etablissement",
        props:{
            rcr: String,
            nom: String
        }
    }
</script>

<style scoped>

</style>
