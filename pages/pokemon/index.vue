<template>
  <div class="flex pl-5">
    <div class="itemsContent flex items-left flex-col justify-left gap-5 w-6/12 scroollbar">
      <ul v-for="(item, index) in result" :key="item.name">
        <li class="items flex gap-5 items-center justify-between">
            <p class="name">{{item.name}}</p>
            <button class="btn btn-primary" v-on:click="loadPokemon(index+1)">Ver</button>
        </li>
      </ul>
    </div>

    <div class="w-6/12 max-h-screen overflow-y-auto" >
        <pokemon :pokemon="pokemon" :show="show"/>
    </div>
  </div>

</template>

<style lang="scss" scoped>
  li{
    max-width: 250px;
  }
  .name{
    text-transform: capitalize;
    font-size: 20px;
  }
  .itemsContent{

    @media(max-width: 992px) {
      max-height: 100vh;
      overflow-y: auto;
    }
    .items{
      @media(max-width: 992px) {
        flex-direction: column;
        align-items: flex-start;

        gap: 5px;
      }
    }

  }
  
</style>

<script>  
import pokemon from '../../components/pokemon.vue'

export default {

  data(){
    return{
      pokemon: null,
      show : false
    }
  },

  components: { pokemon },
 
  async asyncData({ $axios }) {
    const result = (await $axios.$get('/pokemon/')).results
    return { result }

  },
  methods:{
    async loadPokemon(id){
      let pokemon = await this.$axios.$get('https://pokeapi.co/api/v2/pokemon/'+id);
      this.pokemon = pokemon
      this.pokemon.img = pokemon.sprites.front_default 

      this.show = true
    }
  }
}
</script>

