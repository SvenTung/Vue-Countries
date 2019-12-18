<template lang="html">
  <div v-if="country">
    <h3>{{country.name}}</h3>
    <p>Region: {{country.region}}</p>
    <p>Capital: {{country.capital}}</p>
    <p>Population: {{country.population}}</p>
    <label for="languages">Languages:</label>
    <ul name="languages">
      <li v-for="language in country.languages">{{language.name}}</li>
    </ul>
    <img v-bind:src="country.flag" />
  </div>
</template>

<script>
export default {
  name: 'country-detail',
  props: ['country']
}
</script>

<style lang="css" scoped>
h3 {
  margin-top: 0px;
}
img {
  width: 200px;
  border: 2px solid black;
}
</style>
