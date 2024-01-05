<template>

  <h1>homtrete</h1>

  <div class="list-pokemons">
   <div v-for="pokemon in pokeList">
    <p>teste: {{ pokemon.name }}</p>
    <PokeCard :pokeList="pokeList" />     
   </div>
  </div>

  
  
</template>

<script>
import PokeCard from '@/components/PokeCard'
import { onMounted, ref } from 'vue'
import axios from 'axios';

export default {
  name: 'HomeView',
  components: { PokeCard },
  setup(){
    const pokeList = ref([])
    

    /*const pokemonHability = async (singleUrl) => {
      axios.get(singleUrl)
      .then((res) => {      
        pokemonAbilities.value = res.data.abilities[0].ability.name
        console.log(res.data.abilities[0].ability.name)        
      }).catch((err) => {
        console.log(err.message)
      })
    }*/

    onMounted(() => {
      axios.get('https://pokeapi.co/api/v2/pokemon/')
      .then((res) => { 
        console.log(res)     
        pokeList.value = res.data.results
      }).catch((err) => {
        console.log(err.message)
      }).finally(() => {
        console.log('finalmente')
      })
    })

    //console.log(pokeInfo.value)

    /*fetch('https://pokeapi.co/api/v2/pokemon/')
    .then(res => res.json())
    .then(data => pokemons.value = data)*/

    /*onMounted(() => {
      const getData = async () => {
        try{
          let data = await fetch('https://pokeapi.co/api/v2/pokemon/')        
          data = await data.json()        
          pokemons.value = data.results
        }catch(err){
          console.log(err.message)
        }
      }
      getData()  
    })*/
    
    /*onMounted(async () => {
      let response = await fetch('https://pokeapi.co/api/v2/pokemon/');
      response = await response.json();
      pokemons.value = response.results
      console.log(response.results)
    });*/       

    return {pokeList}
  }
}
</script>
