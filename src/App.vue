<template>

  <nav-bar
    @change-component="changeSelectedComponent"
  >
  </nav-bar>

  <keep-alive include="player-view">
    <component 
      :is="selectedComponent"
      v-bind="currentProps"
      @child-event="panierUpdate"
    >
    </component>
  </keep-alive> 
  
</template>


<script>

import ProduitView from './components/ProduitView.vue';
import PanierList from './components/PanierList.vue';
import NavBar from './components/navigation/NavBar.vue';

export default {
  name: 'App',
  components: {
    ProduitView,
    PanierList,
    NavBar
  },
  data() {
    return{
      selectedComponent:'produit-view',
      produitSelection: []
    }
  },
  computed:{
      currentProps(){
        if(this.selectedComponent == "panier-list"){
          return { panier: this.produitSelection }
        }
        return false
      }
  },
  methods:{
    changeSelectedComponent(value){
      this.selectedComponent = value
    },
    panierUpdate(value) {
      this.produitSelection.push(value)
    }
  }
}
</script>

<style>
</style>
