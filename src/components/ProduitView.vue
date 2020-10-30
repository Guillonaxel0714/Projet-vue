<template>
    <div class="flex">
        <div class="w-4/6">
            <produit-list
                v-for="(produit, index) in consommable.produits" 
                :key="index"
                :produit="produit"
                @add-produit="addProduitToPanier"
            >
            </produit-list>
        </div>
        <panier
            title="Panier"
            :panier="panier"
            @delete-produit="deleteProduitToPanier"
        >
        </panier>
    </div>  
</template>

<script>

import produitData from '../data/produits.json';
import ProduitList from './ProduitList.vue';
import Panier from './Panier.vue';

export default {
    name: 'produit-view',
     components: {
    ProduitList,
    Panier
  },
  data(){
    return{
      consommable: produitData,
      panier: []
    }
  },
  methods:{
    addProduitToPanier(produit){
      this.panier.push(produit)
      this.$emit('child-event', produit)
    },
    deleteProduitToPanier(produit){
      this.panier.splice(produit)
    }
  }
}
</script>

<style>

</style>