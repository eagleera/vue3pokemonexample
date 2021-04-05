<template>
  <div>
    <Pokemon :pokemon-id="pokemonId" />
  </div>
</template>

<script>
import Pokemon from "./components/Pokemon2.vue";
export default {
  components: { Pokemon },
  data() {
    return {
      pokemonId: Math.ceil(Math.random() * 500)
    }
  }
}
</script>