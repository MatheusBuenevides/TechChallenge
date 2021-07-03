<template>
  <div class="flex">

    <div class="flex items-left flex-col justify-left gap-5 w-6/12">
      <ul v-for="(item, index) in result" :key="item.name">
        <li>
            <button v-on:click="loadPokemon(index+1)">{{item.name}}</button>
        </li>
      </ul>
    </div>





    <div class="w-6/12 max-h-screen overflow-y-auto">
      <ul v-for="item in pokemon.moves" :key="item.name">
        <li>
            {{item.move.name}}
        </li>
      </ul>
    </div>
  </div>

</template>


<script>  
export default {
  data(){
    return{
      pokemon: []
    }
  },
  async asyncData({ $axios }) {
    const result = (await $axios.$get('/pokemon/')).results
    return { result }

  },
  methods:{
    async loadPokemon(id){
      let pokemon = await this.$axios.$get('https://pokeapi.co/api/v2/pokemon/'+id);
      this.pokemon = pokemon
    }
  }
}
</script>
