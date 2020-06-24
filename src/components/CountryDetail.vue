<template lang="html">
  <div v-if="country !== null">
      <h3>{{country.name}}</h3>
      <p>{{country.capital}}</p>
      <p>{{country.population}}</p>
      <ul>
        <li v-for="(language, index) in languages" :language="language" :key="index">Languages:{{country.languages[0]}}</li>
      </ul>
      <img :src="country.flag" alt="Country Flag"></img>
  </div>
</template>

<script>
export default {
    name:'country-detail',
    props: ['country']
}
</script>

<style>
img{
    width: 15%;
}
</style>