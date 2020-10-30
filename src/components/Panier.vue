<template>
    <div class="border-black border m-5 w-2/6 p-2 bg-indigo-300 h-64">
        <p class="text-center font-bold text-lg p-2"> {{ title }} </p>
        <p>Article : {{ panier.length }}</p>
        <span v-if="numberArticle">Produit</span>
        <span v-else>Produits</span><br>
        
        <ul>
            <li
                v-for="produit in panier"
                :key="produit.nom"
            >
                {{ produit.nom }} (prix: {{ produit.prix }} €)
            </li>
        </ul>

        <p>Montant total : </p>

        <delete-button
            deleteOne="Tout supprimer"
            @click="deleteToPanier"
        >
    </delete-button>
    </div>



</template>

<script>

import DeleteButton from './DeleteButton.vue';

export default {
    name: 'panier',
    props: ['title','panier'],
    components:{
        DeleteButton,
    },
    computed: {
        numberArticle(){
            if(this.panier.length < 2){
                return true
            }
            return false
        }
    },
    methods: {
        deleteToPanier(){
            this.$emit('delete-produit', this.produit.nom)
        }
    }
}
</script>

<style scoped>

</style>