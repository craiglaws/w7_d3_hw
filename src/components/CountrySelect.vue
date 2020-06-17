<template lang="html">
  <div>
    <label for="country-select">Select Country</label>
    <input type="text" id="country-select" v-model="selectedCountry" v-on:keypress="handleChange">
    <!-- <select id="country-select" v-model="selectedCountry" v-on:change="handleChange">
      <country-select-option v-for="(country, index) in countries" :country="country" :key="index"></country-select-option>
    </select> -->
  </div>
</template>

<script>
// import CountrySelectOption from './CountrySelectOption.vue';
import {eventBus} from '../main.js'

export default {
  name: 'country-select',
  // props: ['countries'],
  // components: {
  //   "country-select-option": CountrySelectOption

  data(){
    return {
      selectedCountry: null
    }
  },
  methods: {
    handleChange(){
      eventBus.$emit('selected-country', this.selectedCountry)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
