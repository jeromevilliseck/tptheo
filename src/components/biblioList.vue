<template>
    <div id="toto">
        <ul>
            <input v-model="message" type="text"/>
            <li :key="item.library.rcr" v-for="item in itemFilter"> <!-- Attention c'est désormais obligatoire de rajouter un attribut :key pour attribuer un identifiant unique à chaque élement li-->
                <etablissement :rcr="item.library.rcr" :nom="item.library.shortname"></etablissement>
                <!--[3] Utilisation de la balise du component etablissement qui doit prendre le même nom que dans import [nom] du même fichier-->
                {{ item.rcr }}
            </li>
        </ul>
    </div>
</template>

<script>
    import axios from "axios"; //L'import des components dit système (equivalent à une librairie système java) se fait uniquement npm install [le nom de la library]
    //Si npm install [nom de la library] --safe -dev
    import etablissement from "./etablissement.vue"; //[1] Importer le component enfant avec son chemin : ./ si dans le niveau courant; @ si construction du chemin à parti du dossier src

    export default {
        name: "biblioList", //Le nom choisi à l'export du component
        components: { //[2] Les components importés par ce component que ce dernier va exploiter à travers des balises (= les components enfants de ce component)
            etablissement
        },
        data() { //les membres private de la classe bibliolist
            return {
                items: []
            }
        },
        methods: {
            getList() { //méthode faisant un appel à axios de manière externe pour récupérer la liste
                axios({
                    method: "GET",
                    url: "https://www.idref.fr/services/iln2rcr/5&format=text/json"
                }).then(
                    result => {
                        this.items = result.data.sudoc.query.result;
                    },
                    error => {
                        console.error(error); //equivalent à un syso, interdit en java
                    }
                );
            }
        },
        computed: {
            itemFilter(){ //La fonction est vue comme un membre dans l'utilisation des templates
                this.items.filter() //traitement
            }
        },
        created() { //Les méthodes internes à la classe qui s'appellent automatiquement au moment de la création du component (voir le diagramme lifecycle) : au chargement de la page la méthode sera appelée automatiquement
            this.getList()
        }
    }

</script>

<style scoped>

</style>
