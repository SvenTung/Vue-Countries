<template>
  <div id="app">
      <h1>Countries List</h1>
      <div class="countrylist">
          <countries-list :countries="countries"></countries-list>
          <country-details :country="selectedCountry"></country-details>

      </div>
  </div>
</template>

<script>
import CountriesList from './components/CountriesList.vue'
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

    eventBus.$on('country-selected', (country) => {
      this.selectedCountry = country

    })

  },
  components: {
    'countries-list': CountriesList,
    'country-details': CountryDetails
  }

}
</script>

<style>
.countrylist {
  display: flex;
  justify-content: space-between;
}

</style>
