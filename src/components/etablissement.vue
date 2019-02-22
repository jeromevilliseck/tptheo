<template>
    <span>RCR : {{ rcr }}, NOM : {{ nom }}</span> <!--Les props seront utilisant dynamique dans le composant père en étant déclaré en attribut :nom_props="valeur absolue" ou :nom_props=fonction()-->
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
