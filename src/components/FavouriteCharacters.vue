<template>
  <ul>
      <li v-for="character in favouriteCharacters">{{character.name}}</li>
  </ul>
</template>

<script>
export default {
    name: 'favourite-characters',
    props: ['favouriteCharacters']
}
</script>

<style>
li {

    list-style: none;
    padding: 0;
    font-weight: 500;
    
}
</style>