<template>
    <div v-if="pokemon.sprites">
        <img :src="pokemon.sprites.front_default" alt="pokemon sprite" />
    </div>
    <button @click="randomize">Randomize</button>
</template>
  
<script setup>
import { ref, onMounted } from 'vue'

const props = defineProps({
    pokemonId: Number,
});
let pokemon = ref({})
const getPokemonData = async (pokemonId) => {
    const response = await fetch(`https://pokeapi.co/api/v2/pokemon/${pokemonId}`)
    pokemon.value = await response.json();
}
const randomize = () => {
    getPokemonData(Math.ceil(Math.random() * 500));
}
onMounted(getPokemonData(props.pokemonId));
</script>