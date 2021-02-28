<template>
  <div>
    <div v-if='character'>
        <h2>{{character.name}}
            <button v-on:click='handleAddClick'>Add to favourites</button>
        </h2>
        <p>Nickname: {{character.nickname}}</p>
        <p>Occupation: {{character.occupation}}</p>
        <p>Status: {{character.status}}</p>
    </div>
  </div>
</template>

<script>
import {eventBus} from '../main.js'

export default {
    name:'character-detail',
    props: ['character', 'favouriteCharacters'],
    methods: {
        handleAddClick() {
            eventBus.$emit('character-add', this.character)
        }
    }
}
</script>

<style>

</style>