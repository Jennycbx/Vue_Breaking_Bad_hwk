<template>
  <form>
        <select v-on:change="handleSelect" v-model='selectedCharacter'>
            <option disabled value="">Select a character</option>
            <option v-for='(character, index) in characters' :key='index' :value="character">{{character.name}}</option>
        </select>
    </form>
</template>

<script>
import {eventBus} from '../main.js'

export default {
    name: 'characters-list',
    data() {
        return {
            'selectedCharacter': {}
        }
    },
    props: ['characters', 'favouriteCharacters'],
    methods: {
        handleSelect() {
            this.search = ""
            eventBus.$emit('character-selected', this.selectedCharacter)
        }
    },
    components: {
    }
}
</script>

<style>
select {
    height: 30px;
    background-color: rgb(245, 2, 2);
    border-radius: 12px;
    padding-left: 10px;
    
}
</style>
