<template>

    <div>
        <div class="flex justify-between mr-5 items-center">
            <img v-bind:src="pokemon.img">
            <h1 class="pageTitle">{{pokemon.name}}</h1>
            <nuxt-link :to="`/pokemon`" class="btn btn-primary">
                Voltar
            </nuxt-link>
        </div>
        <div class="flex gap-10">
            <div class="items w-1/3 pl-3">
                <h3 class="mb-5">Abilidades</h3>
                <ul>
                    <li v-for="item in pokemon.abilities" :key="item.name">
                        {{item.ability.name}}
                    </li>
                </ul>
            </div>

            <div class="items w-1/3 pl-3">
                <h3 class="mb-5">Movimentos</h3>
                <ul class="h-40 overflow-y-auto">
                    <li v-for="item in pokemon.moves" :key="item.name">
                        {{item.move.name}}
                    </li>
                </ul>
            </div>

            <div class="items w-1/3 pl-3">
                <h3 class="mb-5">Tipos</h3>
                <ul class="h-40 overflow-y-auto">
                    <li v-for="item in pokemon.types" :key="item.name">
                        {{item.type.name}}
                    </li>
                </ul>
            </div>

        </div>

        


    </div>
    
</template>

<script>
export default {

    async asyncData({$axios, params}) {
        let pokemon = (await $axios.get(`/pokemon/${params.id}`)).data
        pokemon.img = pokemon.sprites.front_default 
        return { pokemon }
    },
}
</script>

<style scoped>
    .pageTitle{
        color: #f6bd20;
        font-size: 35px;
    }

    .items{
        border-left: solid 2px #f6bd20;
    }

    h3{
        font-size: 20px;
        font-weight: bold;
        color: #f6bd20;
    }

    li{
        font-weight: lighter;
    }
</style>