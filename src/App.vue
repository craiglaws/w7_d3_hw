<template lang="html">
  <div class="main-container">
    <h2>Country Finder</h2>
    <div>
    <country-select :countries='countries'></country-select>
  </div>
  <div>
    <country-selected-detail v-if="selectedCountry" :country='selectedCountry'></country-selected-detail>
  </div>
  </div>
</template>

<script>
import {eventBus} from './main.js';
import CountrySelect from './components/CountrySelect.vue';
import CountrySelectedDetail from './components/CountrySelectedDetail.vue'
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
    .then(result => result.json())
    .then(data => this.countries = data)

    eventBus.$on('selected-country', (country) => {
      this.selectedCountry = country
    })
  },

  components: {
    "country-select": CountrySelect,
    "country-selected-detail": CountrySelectedDetail
  }
}
</script>

<style lang="css" scoped>


.main-container{
  width: 80vw;
  margin: auto;
  height: 100vh;
  background-color: lightGray;
  justify-content: center;
  
}

.detail{
  margin: auto;
}

body{
  background-color: red;
}
</style>
