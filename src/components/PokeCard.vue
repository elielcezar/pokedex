<template>        
    
    <div class="card">
        <img :src="image" :alt="pokemon.name">
        <h2>{{ pokemon.name }}</h2>    
        <p>{{ pokemon.url }}</p>            
        <div class="info">
            <h4>Tipo:</h4>
            <p>{{ type }}</p>
            <h4>Poderes:</h4>
            <ul>
                <li v-for="abili in abilities">
                    {{ abili.ability.name }}
                </li>
            </ul>
        </div>
    </div>
    
</template>

<script>
import { onMounted, ref } from 'vue'
import axios from 'axios';

export default {
    name: 'PokeCard',
    props: ['pokemon'],
    setup(props){        
        const image = ref('')
        const abilities = ref([])
        const type = ref('')

        onMounted(() => {            
            axios.get(props.pokemon.url)
            .then((res) => {     
                image.value = res.data.sprites.other.home.front_default           
                abilities.value = res.data.abilities
                type.value = res.data.types[0].type.name
            }).catch((err) => {
                console.log(err.message)
            })                     
        })

        return {abilities, type, image}
    }
}
</script>

<style>



</style>