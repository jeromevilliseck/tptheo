<template>
    <div>
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
    import axios from "axios";
    //L'import des components dit système (equivalent à une librairie système java, ceux qui n'ont pas ete cres par le dev)
    //se fait uniquement npm install [le nom de la library]
    //[commande] npm install [nom de la library] --safe -dev

    import etablissement from "./etablissement.vue";
    //[1] Importer le component enfant avec son chemin :
    // ./ si dans le niveau courant;
    // @ si construction du chemin à parti du dossier src

    export default {
        name: "biblioList", //nom public du composant
        components: {
            etablissement //[2] Composants qui constituent le composant bibliolist
        },
        data() { //membres privés du composant en cours
            return {
                items: [],
                message: ""
            }
        },
        methods: {
            getList() { //méthode faisant un appel à axios de manière externe pour récupérer la liste
                axios({
                    method: "GET",
                    url: "https://www.idref.fr/services/iln2rcr/5&format=text/json"
                }).then(
                    result => {
                        this.items = result.data.sudoc.query.result; //[affectation] impacte le membre privé items
                    },
                    error => {
                        console.error(error); //equivalent à un syso, interdit en java
                    }
                );
            }
        },
        computed: {
            itemFilter() { //La fonction est vue comme un membre dans l'utilisation des templates
                return this.items
            }
        },
        created: function() {
            //Les méthodes internes à la classe qui s'appellent automatiquement au moment de la création du component
            // (voir le diagramme lifecycle) : au chargement de la page la méthode sera appelée automatiquement
            this.getList() //appelle automatiquement this.getList() au chargement de la page
        }
    }

</script>

<style scoped>

</style>
