<template lang="html">
  <div>
    <select v-on:change="handleChange" v-model="countrySelected">
      <option v-bind:value="country" v-for="country in countries">{{country.name}}</option>
    </select>
  </div>
</template>

<script>
  import {eventBus} from '../main.js'
  export default {
    name: 'countries-select',
    data(){
      return{
        countrySelected:null
      }
    },
    props: ['countries', 'country', 'selectedCountry'],
    methods: {
      handleChange(){
        eventBus.$emit('selectedCountry', this.countrySelected)
      }
    }
  }
</script>

<style lang="css" scoped>

</style>
