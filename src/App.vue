<template>
  <div id="app">
    <h1>Breaking Bad Characters</h1>
    <characters-list :characters='characters'></characters-list>
    <character-detail :character='selectedCharacter'></character-detail>
    <h2 id='favourite-characters'>Favourite Characters</h2>
    <favourite-characters :favouriteCharacters='favouriteCharacters'></favourite-characters>
  </div>
</template>

<script>
import CharactersList from './components/CharactersList.vue'
import CharacterDetail from './components/CharacterDetail.vue'
import FavouriteCharacters from './components/FavouriteCharacters.vue'

import {eventBus} from './main.js'

export default {
  name: 'App',
  data() {
    return {
      characters: [],
      favouriteCharacters: [],
      selectedCharacter: null
    }
  },

  components: {
    'characters-list': CharactersList,
    'character-detail': CharacterDetail,
    'favourite-characters': FavouriteCharacters
  },

  mounted() {
    fetch("https://breakingbadapi.com/api/characters")
    .then(res => res.json())
    .then(characters => this.characters = characters)

    eventBus.$on('character-selected', (character) => {
      this.selectedCharacter = character
    }),

    eventBus.$on('character-add', (character) => {
      this.handleAddClick(character)
    })

  },

  methods: {
    handleAddClick: function(character) {
      this.favouriteCharacters.push(this.selectedCharacter)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #380101;
  margin-top: 60px;
}

body {
  background-image: url(https://media.wired.com/photos/5b33447fa2bff9692c40a1fc/master/w_1600%2Cc_limit/BB_2.jpg);
  background-size: cover;
  background-repeat: no-repeat;
  margin: 30px;
}
</style>
