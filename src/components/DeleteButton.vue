<template>
    <button class="btn-red">
        {{ deleteOne }}
    </button>
</template>




<script>

export default {
    name: 'delete-button',
    props: ['deleteOne']
}
</script>



<style scoped>

.btn-red {
  @apply bg-red-500 text-white font-bold py-2 px-4 rounded;
}
.btn-red:hover {
  @apply bg-red-700;
}

</style>