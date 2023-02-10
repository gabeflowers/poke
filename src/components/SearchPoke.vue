<template>
  <header class="header">
    <label>
      Digite o nome de um Pokemon ou seu ID:
      <input type="text" id="" v-model="pokemonID">
      <button
        class="searchButton"
        @click="searchPokemon"
      >
        Search Pokemon
      </button>
      <button @click="clearInput" class="clearButton"> clear </button>
    </label>
  </header>
</template>

<script>
import { pokeapi } from '@/api/pokeapi';

export default {
    name: 'SearchPoke',
    data() {
      return {
        pokemonData: {},
        pokemonID: '',
      }
    },
    methods: {
      async searchPokemon() {
        if (!this.pokemonID || !this.pokemonID.trim()) {
          alert('O campo deve estar preenchido corretamente.')
          return
        }
        try {
            const pokemonToFind = await fetch(`${pokeapi}/${this.pokemonID}`)
            const pokemon = await pokemonToFind.json()
            this.pokemonData = pokemon
            console.log(pokemon)
            this.$emit('update-pokemon-data', pokemon)
        } catch (error) {
            alert('pokemon not found')
        }
      },
      clearInput(){
        this.pokemonData = {};
        this.pokemonID = '';
        this.$emit('delete-pokemon-data');
      }, 
    },
}
</script>

<style lang="scss" scoped>
@import '@/pokemon_types.scss';

.header, input[type="text"], .searchButton {
    font-family: 'Changa', sans-serif;
    font-size: 1.5rem;
}
.header, input[type="text"], .clearButton {
    font-family: 'Changa', sans-serif;
    font-size: 1.5rem;
}
.header {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100px;
  background-color: $pokedex-blue;
  color: white;
  & .searchButton {
    background-color: #1cb02b;
    color: white;
    border: none;
    margin-left: 10px;
    border-radius: 10px;
    cursor: pointer;
    &:hover {
      background-color: #1c8b0a;
    }
  }
  & .clearButton {
    background-color: $pokedex-red;
    color: white;
    border: none;
    margin-left: 10px;
    border-radius: 10px;
    cursor: pointer;
    &:hover {
      background-color: #cc0000;
    }
  }
  & input[type="text"] {
    border-radius: 10px;
    outline: none;
    border: none;
  }
}

@media screen and (max-width: 820px) {
  .header {
    flex-direction: column;
    height: 120px;
    & .searchButton {
      width: 70%;
      margin-top: 10px;
    }
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
}

@media screen and (max-width: 400px) {
  .header {
    & label {
      text-align: center;
    }
  }
}
</style>
