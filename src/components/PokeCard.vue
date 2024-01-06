<template>        
    
    <div class="card" :id="pokeId">
        <div class="image">
            <img :src="image" :alt="pokemon.name">
        </div>
        <div class="info">
            <h2>{{ pokemon.name }}</h2>            
            <div class="info">            
                <ul class="type">
                    <li v-for="tipo in types" :class="tipo.type.name">
                        {{ tipo.type.name }}
                    </li>                
                </ul>
                
                <ul class="abilities">
                    <li v-for="abili in abilities">
                        {{ abili.ability.name }}
                    </li>
                </ul>
            </div>
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
        const types = ref([])
        const pokeId = ref('')        

        onMounted(() => {            
            axios.get(props.pokemon.url)
            .then((res) => {     
                image.value = res.data.sprites.other.home.front_default           
                abilities.value = res.data.abilities
                types.value = res.data.types                   
                pokeId.value = 'pokemon-' + props.pokemon.url.split('/')[6]                
            }).catch((err) => {
                console.log(err.message)
            })                     
        })

        return {abilities, types, image, pokeId}
    }
}
</script>

<style scoped>
.card{
    border: 2px solid var(--light-blue);
    text-align: center;
    border-radius: 20px;
    margin: 15px auto;
    
    @media(orientation:landscape){
        max-width: 23%;
        margin: 0 2.6% 25px 0;
        &:nth-child(4n){
            margin-right: 0;
        }
    }

    .image{
        display: flex;
        align-items: center;
        justify-content: center;
        padding: 5% 5% 15% 5%;        
        border-bottom: 2px solid var(--light-blue);
        background: transparent url(../assets/img/bg-pokeball.png) center no-repeat;

        img{
            margin-bottom: -10%;
        }
    }
    .info{
        padding: 5%;
    }
}
</style>