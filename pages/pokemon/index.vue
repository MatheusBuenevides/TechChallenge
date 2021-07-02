<template>
  <div class="flex items-center flex-col h-screen justify-center gap-5">

    <h1 class="pageTitle">Olá!</h1>

    <ul v-for="item in data" :key="item.name">
        <li>
            {{item.name}}
        </li>
    </ul>
    
    
  </div>

</template>

<script>
export default {

  async asyncData({ $axios }) {
    const data = (await $axios.$get('/pokemon/')).results
    return { data }

  }


}
</script>
