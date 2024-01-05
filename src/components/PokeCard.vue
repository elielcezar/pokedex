<template>
    <div class="project">
        <div class="actions">
            <!--h3>namne: {{ pokeInfo.name }}</h3>
            <p>url: {{ pokeInfo.url }}</p>
            <p>ability: {{ ability }}</p-->
        </div>      
    </div>
</template>

<script>
import { onMounted, ref } from 'vue'
import axios from 'axios';

export default {
    name: 'PokeCard',
    props: ['pokeList'],
    setup(props){
        const singleUrl = ref(props.url) 
        const ability = ref([])
        
        const pokemonHability = async () => {
            axios.get(singleUrl)
            .then((res) => {
                
            }).catch((err) => {
                console.log(err.message)
            })
        }
        //pokemonHability()
        console.log('singleurl: ' + JSON.stringify(singleUrl))

        return{ability, singleUrl}
    }
}
</script>

<style>



</style>