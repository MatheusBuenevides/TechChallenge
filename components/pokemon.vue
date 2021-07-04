<template>
    <div v-if="show" class="flex flex-col h-screen items-center justify-center">
        <img v-bind:src="pokemon.img" alt="">
        
        <h1 class="pageTitle">{{pokemon.name}}</h1>
        <div class="flex gap-5">
          <p class="text-center">Altura: {{pokemon.height}}</p>
          <p class="text-center">Peso: {{pokemon.weight}}</p>
        </div>
        <div class="m-3">
            <nuxt-link :to="`/pokemon/`+pokemon.id" class="btn btn-primary"> Mais detalhes </nuxt-link>
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

