<template>
    <div class="border-black border m-5 p-2 flex justify-between" :class="outOfStock">
        <div>
            <h1 class="text-xl font-bold">{{ produitNomUp }}</h1>
            <h2>Prix : {{ produit.prix }}€</h2>
            <h2>Quantité : <span :class="quantiteStyle">{{ produit.quantite }}</span></h2>
            <p>Catégorie : <span :class="categorieStyle">{{produit.categorie }}</span></p>
            <base-button
                text="Ajouter"
                :isDisabled="stockArticle"
                :class="disabledButton"
                @click="addToPanier"
            >
            <span></span>
            </base-button>
        </div>
        <div class="w-32">
            <img :src="produit.image" alt="image produit" />
        </div>
    </div>
</template>

<script>
export default {
    name: 'produit-list',
    props: ['produit'],
    computed:{
        produitNomUp(){
            return this.produit.nom.toUpperCase()
        },
        stockArticle(){
            if(this.produit.quantite == "0"){
                return true
            }
            return false
        },
        outOfStock(){
            return{
                'bg-gray-600': this.stockArticle,
                'border-white': this.stockArticle,
                'border-black': !this.stockArticle,
            }
        },
        quantiteStyle(){
            return{
                'text-red-500': this.stockArticle,
                'text-balck-500': !this.stockArticle
            }
        },
        disabledButton(){
            return{
                'bg-blue-500 text-white font-bold py-2 px-4 rounded opacity-50 cursor-not-allowed': this.stockArticle,
            }
        },

        fruitOuLegume(){
            if(this.produit.categorie == "fruit"){
                return true
            }
            return false
        },
        categorieStyle(){
            return{
                'text-blue-500': this.fruitOuLegume,
                'text-green-500': !this.fruitOuLegume
            }
        },
    },
    methods:{
        addToPanier(){
            this.$emit('add-produit', this.produit)
        },
    }
}
</script>

<style scoped>

</style>>

