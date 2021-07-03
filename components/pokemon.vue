<template>
    <div v-if="show" class="flex flex-col h-screen items-center justify-center">
        <img v-bind:src="pokemon.img" alt="">
        
        {{pokemon.name}}
        <div>
          <p>Altura: {{pokemon.height}}</p>
          <p>Peso: {{pokemon.weight}}</p>
        </div>

      </div>
</template>

<script>
export default {
    props: {
        pokemon: Object,
        show: Boolean
    }
}
</script>

<style>

</style>