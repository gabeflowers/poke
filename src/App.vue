<template>
<<<<<<< HEAD
  <div class="imageLogo">
    <img :src="PokemonLogo" alt="Logo do Pokemon">
  </div>
  <SearchPoke @update-pokemon-data="updatePokemonData" @delete-pokemon-data="clearPokemon"/>
  <main 
  class="main"
  v-if="Object.entries(pokemonData).length > 0 && quero"  
  >
    <section class="pokemonCard">
      <div class="nameImage">
        <h1 class="pokemonName">{{ pokemonData.name }}</h1>
        <img :src="pokemonData.sprites.front_default" :alt="pokemonData.name">
      </div>
      <ul class="type">
        <h2>Type:</h2>
        <li
        v-for="(type, index) in pokemonData.types"
        :key="index"
        :class="type.type.name"
        >
        <span>{{ type.type.name }}</span>
      </li>
      </ul>
      <ul class="stats">
        <h2>stats:</h2>
        <li
        v-for="(stat, index) in pokemonData.stats"
        :key="index"
        >
        <span> {{ stat.stat.name }} -> {{ stat.base_stat }}</span>
      </li>
      </ul>
    </section>
  </main>
</template>

<script>
import SearchPoke from '@/components/SearchPoke.vue';
import Logo from '@/assets/pokemon-logo.png';

export default {
  name: 'App',
  data() {
    return {
      pokemonData: {},
      pokemonID: '',
      quero: false,
      PokemonLogo: Logo,
    }
  },
  components: {
    SearchPoke,
  },
  methods: {
    updatePokemonData(pokemon) {
      this.quero = true;
      this.pokemonData = pokemon;
    },
    clearPokemon(){
      this.quero = false;
      this.pokemonData = {};
      this.pokemonID = '';
    }
  },
}
</script>


<style lang="scss" scoped>
@import './pokemon_types.scss';
@import url('https://fonts.googleapis.com/css2?family=Changa:wght@400;700&display=swap');

.main {
  font-size: 1.2rem;
  background-color: $pokedex-green;
}

.pokemonCard {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  align-content: center;
  & .nameImage, & .type, & .stats {
    width: 33%;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
  }
  & .nameImage {
    & .pokemonName {
      text-transform: capitalize;
    }
    & img {
      width: 200px;
      background-color: $pokedex-blue;
      border-radius: 50%;
    }
  }
  & .type li {
    width: 90%;
    margin-bottom: 10px;
    text-align: center;
    border-radius: 20px;
  }
  & .stats li {
    align-self: flex-start;
  }
}
ul {
  padding: 0;
}
.type {
  & li {
    list-style: none;
    color: white;
    text-transform: uppercase;
  }
}
.stats {
  color: black;
  & li {
    list-style: none;
    text-transform: uppercase;
  }
}
.imageLogo {
  width: 55%;
  margin: auto;
}
img {
  max-width: 100%;
}
.normal {
  background-color: $normal
}
.fire {
  background-color: $fire
}
.water {
  background-color: $water
}
.grass {
  background-color: $grass
}
.electric {
  background-color: $electric
}
.ice {
  background-color: $ice
}
.fighting {
  background-color: $fighting
}
.poison {
  background-color: $poison
}
.ground {
  background-color: $ground
}
.flying {
  background-color: $flying
}
.psychic {
  background-color: $psychic
}
.bug {
  background-color: $bug
}
.rock {
  background-color: $rock
}
.ghost {
  background-color: $ghost
}
.dark {
  background-color: $dark
}
.dragon {
  background-color: $dragon
}
.steel {
  background-color: $steel
}
.fairy {
  background-color: $fairy
}
@media screen and (max-width: 820px) {
  .pokemonCard {
    flex-direction: column;
    align-items: center;
  }
}
@media screen and (max-width: 600px) {
  .header {
    font-size: 1rem;
    & input[type="text"] {
      font-size: 1rem;
    }
    & .searchButton {
      font-size: 1rem;
    }
  }
  .pokemonCard {
    & .stats {
      width: 90%;
    }
  }
}

=======
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
>>>>>>> origin/master
</style>
