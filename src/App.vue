<template lang="html">
  <div class="main-container">
    <h2>Country Finder</h2>
    <div>
    <!-- <country-select :countries='countries'></country-select> -->
    <country-select> </country-select>
  </div>
  <div>
    <country-selected-detail v-if="searchCountries.length === 1" :country='searchCountries[0]'></country-selected-detail>
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
      selectedCountry: null,
      countriesSearch: []
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
  },

  computed: {
    searchCountries(){
      if (this.selectedCountry !== null){
      return this.countries.filter(country => country.name.toLowerCase().includes(this.selectedCountry.toLowerCase()))
    }else return "null"
  }
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
