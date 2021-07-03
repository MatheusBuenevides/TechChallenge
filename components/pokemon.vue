<template>
    <div v-if="show" class="flex flex-col h-screen items-center justify-center">
        <img v-bind:src="pokemon.img" alt="">
        
        <h1 class="pageTitle">{{pokemon.name}}</h1>
        <div class="flex gap-5">
          <p>Altura: {{pokemon.height}}</p>
          <p>Peso: {{pokemon.weight}}</p>
        </div>

      </div>
</template>

<style>
    p{
        font-size: 18px;
    }    
</style>

<script>
export default {
    props: {
        pokemon: Object,
        show: Boolean
    }
}
</script>

