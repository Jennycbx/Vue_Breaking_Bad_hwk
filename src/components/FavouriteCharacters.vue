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

</style>