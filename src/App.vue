<template>
  <div id="app">
    <h1>Countries</h1>
    <div class="country-select">
      <countries-select :countries="countries"></countries-select>
      <country-details :country="selectedCountry"></country-details>
    </div>
  </div>
</template>

<script>
  import CountriesSelect from './components/CountriesSelect.vue'
  import {eventBus} from './main.js'
  import CountryDetails from './components/CountryDetails.vue'

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

      eventBus.$on('selectedCountry', (country) => {
        console.log(country);
        this.selectedCountry = country
      })
    },
    components: {
      'countries-select': CountriesSelect,
      'country-details': CountryDetails
    }
  }
</script>

<style>
h1{
  display: flex;
  justify-content: center;
}
.country-select {
  display: flex;
  justify-content: space-around;
}
</style>
