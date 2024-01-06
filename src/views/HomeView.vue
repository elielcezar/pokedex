<template>  
  <div class="list-pokemons">   
    <PokeCard :pokemon="pokemon" v-for="pokemon in pokeList" :key="pokemon.name" />        
  </div>  
</template>

<script>
import { onMounted, ref } from 'vue'
import axios from 'axios';
import PokeCard from '@/components/PokeCard.vue'

export default {
  name: 'HomeView',  
  components: {PokeCard},
  setup(){
    const pokeList = ref([])    

    onMounted(() => {
      axios.get('https://pokeapi.co/api/v2/pokemon/')
      .then((res) => {         
        pokeList.value = res.data.results        
      }).catch((err) => {
        console.log(err.message)
      }).finally(() => {
        //console.log('finalmente')
      })
    })

    return {pokeList}
  }
}
</script>
