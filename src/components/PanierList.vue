<template>
  <div class="container w-4/5 mx-auto mt-4">
    <h1 class="text-lg font-bold">Ms articles</h1>

    <div v-if="panier.length == 0">
      <p>Aucun article sélectionné</p>
    </div>
    <div v-else>
        <div
            v-for="produit in panier"
            :key="produit.nom" 
            class="border border-black my-4 p-2"
        >
            <h3> {{ produit.nom }} </h3>
            <p> {{ produit.prix }} € </p>  
            <p> {{ produit.categorie }} </p> 

        </div>
    </div>

  </div>
</template>

<script>
export default {
    name: 'panier-list',
    props: ['panier'],

}
</script>

<style>

</style>