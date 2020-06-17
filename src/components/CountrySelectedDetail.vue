<template lang="html">
  <div class="detail">
    <h3>{{country.name}}</h3>
    <p>Capital: {{country.capital}}</p>
    <p>Population: {{country.population}}</p>
    <p>Languages:</p>
    <ul v-for="(info, index) in country.languages" :key="index">
      <li >{{info.name}}</li>
    </ul>
    <img :src="country.flag" class="flag">

  </div>
</template>

<script>
export default {
  name: 'country-selected-detail',
  props: ['country']
}
</script>

<style lang="css" scoped>
.flag{
  height: 50px;
  width: 75px;
}

.detail{
  margin:auto;
}
</style>
