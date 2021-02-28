<template>
  <div id="app">
    <h1>Breaking Bad Characters</h1>
    <characters-list :characters='characters'></characters-list>
    <character-detail :character='selectedCharacter'></character-detail>
  </div>
</template>

<script>
import CharactersList from './components/CharactersList.vue'
import CharacterDetail from './components/CharacterDetail.vue'

import {eventBus} from './main.js'

export default {
  name: 'App',
  data() {
    return {
      characters: [],
      selectedCharacter: null
    }
  },

  components: {
    'characters-list': CharactersList,
    'character-detail': CharacterDetail
  },

  mounted() {
    this.getCharacters()
  },

  methods: {
    getCharacters: function(){
      fetch("https://breakingbadapi.com/api/characters")
      .then(res => res.json())
      .then(characters => this.characters = characters)
    }
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
</style>
