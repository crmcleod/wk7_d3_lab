<template>
  
</template>

<script>
export default {
  name: 'app',
  data(){
    return {
      countries: [],
      selectCountry: null
    };
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(res => res.json())
    .then(countries => this.countries = countries)
  }

}
</script>

<style>

</style>
