<template>
  <div id="app">
    {{"country: " + country}}
    <country-select v-model="country" :country="country" topCountry="India" :countryName="true" />
    {{"region: " + region}}
    <region-select v-model="region" :country="country" :region="region" :countryName="true" :regionName="true" />
  </div>
</template>

<script>
import CountrySelect from '@/components/country-select'
import RegionSelect from '@/components/region-select'

// ***** For demo testing only *****
export default {
  name: 'app',
  components: {
    CountrySelect,
    RegionSelect
  },
  data: () => ({
    country: 'India',
    region: 'Maharashtra'
  })
}
</script>

<style>
#app {
  font-family: Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
