<template>
  <div>
    <div v-if=!character>
        <p>Select a character</p>
    </div>
    <div v-if='character'>
        <h2>{{character.name}}</h2>
        <p>Nickname: {{character.nickname}}</p>
        <p>Occupation: {{character.occupation}}</p>
        <p>Status: {{character.status}}</p>
    </div>
  </div>
</template>

<script>
export default {
    name:'character-detail',
    props: ['character']
}
</script>

<style>

</style>