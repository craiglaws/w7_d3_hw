<template lang="html">
  <!-- <li v-on:click="handleClick">{{country.name}}</li> -->
  <option :value="country">{{country.name}}</option>
</template>

<script>
// import {eventBus} from '../main.js'

export default {

  name: 'country-select-option',
  props: ['country']
  // methods: {
  //   handleClick(){
  //     eventBus.$emit('selected-country', this.country)
  //   }
  // }
}
</script>

<style lang="css" scoped>
</style>
