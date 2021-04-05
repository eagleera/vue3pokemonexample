<template>
    <div v-if="pokemon.sprites">
        <img :src="pokemon.sprites.front_default" alt="pokemon sprite" />
    </div>
    <button @click="randomize">Randomize</button>
</template>
  
  <script>
import { ref, onMounted } from 'vue'

export default {
    props: {
        pokemonId: Number
    },
    setup(props) {
        let pokemon = ref({})
        const getPokemonData = async (pokemonId) => {
            const response = await fetch(`https://pokeapi.co/api/v2/pokemon/${pokemonId}`)
            pokemon.value = await response.json();
        }
        onMounted(getPokemonData(props.pokemonId));
        return {
            pokemon,
            getPokemonData
        }
    },
    methods: {
        randomize() {
            this.getPokemonData(Math.ceil(Math.random() * 500));
        }
    }
}
</script>