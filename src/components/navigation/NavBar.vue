<template>
    <div class="bg-indigo-300 p-2 text-center">
        <a href="#" @click="changeComponent('produit-view')">Tous les produits</a> |
        <a href="#" @click="changeComponent('panier-list')">Mes articles en détails</a>
    </div>
</template>

<script>
export default {
    name: 'nav-bar',
    methods:{
        changeComponent(value) {
            this.$emit('change-component', value)
        }
    }
}

</script>

<style scoped>

</style>