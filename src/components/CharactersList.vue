<template>
  <form>
        <select v-on:change="handleSelect" v-model='selectedCharacter'>
            <option disabled value="">Select a character</option>
            <option v-for='(character, index) in characters' :key='index' :value="character">{{character.name}}
                <!-- <span v-if='favouriteCharacters.includes(character)'>&#127775;</span> -->
            </option>
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
        // "list-item": ListItem
    }
}
</script>

<style>

