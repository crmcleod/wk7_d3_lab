<template lang="html">
  <div>
    <h1>Countries</h1>
      <select id="country_select" v-model="selectedCountry">
        <option disabled value="">Select a country</option>
        <option v-for="country in countries" :value="country">{{country.name}}</option>
      </select>
    <div class="main-container">
      <country-detail :country="selectedCountry"></country-detail>
    </div>
  </div>
</template>

<script>
import CountriesList from './components/CountriesList';
import CountryDetail from './components/CountryDetail';
import {eventBus} from './main.js';

export default {
  name: 'app',
  data(){
    return {
      countries: [],
      selectedCountry: null
    };
  },
  mounted(){
    fetch('https://restcountries.eu/rest/v2/all')
    .then(res => res.json())
    .then(countries => this.countries = countries)

    eventBus.$on('country-selected', (country)=>{
      this.selectedCountry  = country
    })
  },
  components: {
    "countries-list": CountriesList,
    "country-detail": CountryDetail
  }

}
</script>

<style>
    .main-container {
    display: flex;
    justify-content: space-between;
  }
</style>
