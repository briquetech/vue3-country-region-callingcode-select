# Vue3-Country-Region-Select ![CI status](https://img.shields.io/badge/build-passing-brightgreen.svg)

This project provides a pair of Vue 3 components that will allow you to easily put a country and region dropdown in your project that will work together or standalone. Supports vue-i18n.

This project is an eventual fork of the following projects:
1. Original [Vue-Country-Region-Select](https://github.com/gehrj/vue-country-region-select) for Vue 2 by [Justin Gehr](https://github.com/gehrj). If you are looking for Vue 2 support, that is where you want to look.

2. Credit goes to [Justin Gehr](https://github.com/gehrj) and the other contributors for the creation of the original [Vue-Country-Region-Select](https://github.com/gehrj/vue-country-region-select). This fork just provides compatibility with Vue 3.

3. Ittai Svidler for the enhanced version (https://github.com/isvidler/vue3-country-region-select/)

## Installation
`npm install vue3-country-region-calling-code-select --save`

## Dependencies 
Being that these are Vue components you will need to use them inside of Vue.

The Data for the countries and regions are originally taken from: https://www.npmjs.com/package/country-region-data
However the data set is now located in this project and is available to be edited to suit more countries and regions as you need.

## Usage
Here is a sample use case of how you would use vue3-country-region-calling-code-select in your vue project. You can alternatively store the data in a store somewhere. Country and Region values will be returned in their short code values by default. 

Ex. country: 'US' and region: 'IL'

There is a prop that will allow for country to be returned in full instead of in short code version.

The library registers the components globally so only need to import the library once in order to make the components be available throughout your project.

#### main.js
```javascript
import { createApp } from 'vue'
import App from './App.vue'
import vueCountryRegionCallingCodeSelect from 'vue3-country-region-callingcode-select'

const app = createApp(App);
app.use(vueCountryRegionCallingCodeSelect);
app.mount('#app');
```

### Inside component
```vue
<template>
  <country-select v-model="country" :country="country" topCountry="US" />
  <region-select v-model="region" :country="country" :region="region" />
</template>
```
```javascript
export default {
  name: 'MyComponent',
  data: () => ({
    country: '',
    region: ''
  })
}
```

## Options
Here are the available attributes that can be used with the provided components.

```<country-select />```

Parameter | Required? | Default | Type | Description
--------- | --------- | ------- | -------- | ----------
v-model | yes | ''| string | The data binding for your component
country | yes | '' | string | Make this tied to the same piece of data as v-model
topCountry | no | '' | string | By providing this value you will tell component what country to put at the top of the dropdown list for easy selection. Make sure to use country short code. So for United states you would provide 'US'. However, if you set countryName to true make sure to also write out full country name when setting a topCountry. In this scenerio United States would be 'United States'.
countryName | no | false | boolean | By setting this value to true, country names will be output in full instead of using the abbreviated short codes. Make sure to set this true for both country and region if you are using.
whiteList | no | [] | array | Fill this array with capitalized short codes of the countries you want to appear in the dropdown list. ex: ['US', 'CA', 'MX']
blackList | no | [] | array | Fill this array with capitalized short codes of the countries you want to remove from dropdown list. ex: ['US'] 
className | no | '' | string | Class name ex: `form-control`
placeholder | no | 'Select Country' | string | The placeholder text for country select
autocomplete | no | false | boolean | Set to true to enable browser to automatically fill out the country.
returnValue | no | 'country' | string | 'country' to return the Country Name, 'shortcode' to return the Country Short Code, 'callingcode' to return the Country calling code
shortCodeDropdown | no | false | boolean | Use this to have dropdown text display as short codes
showCallingCode | no | false | boolean | Use this to have dropdown text display the country's calling code 
usei18n | no | true | boolean | Set to false if using i18n and want to disable for this component
disablePlaceholder | no | false | boolean | Set to true to make placeholder non-selectable
removePlaceholder | no | false | boolean | Set to true to remove placeholder all together, this will autoselect first in list automatically

```<region-select /> ```

Parameter | Required? | Default | Type | Description
--------- | --------- | ------- | -------- | ----------
v-model | yes | ''| string | The data binding for your component
region | yes | '' | string | Make this tied to the same piece of data as v-model
country | no | '' | string | This tells the component what country to grab the list of displayed regions from. To have it work in tandem with country component provide it the variable that is tied to the v-model of the country-select component.
defaultRegion | no | 'US' | string | This allows you to set a default region when choosing not to use the country attribute. It will be set to regions of the United States if not provided.
countryName | no | false | boolean | Set this to true if you are setting it to true while using Country Select. This is just to help keep the data values in sync.
regionName | no | false | boolean | Set this to true if you want the v-model to output full region names instead of the default abbreviations.
whiteList | no | [] | array | Fill this array with capitalized short codes of the regions you want to appear in the dropdown list. ex: ['AL', 'AK', 'WA']
blackList | no | [] | array | Fill this array with capitalized short codes of the regions you want to remove from dropdown list. ex: ['AZ'] 
className | no | '' | string | Class name ex: `form-control`
placeholder | no | 'Select Region' | string | The placeholder text for region select
autocomplete | no | false | boolean | Set to true to enable browser to automatically fill out the region.
shortCodeDropdown | no | false | boolean | Use this to have dropdown text display as short codes
usei18n | no | true | boolean | Set to false if using i18n and want to disable for this component
disablePlaceholder | no | false | boolean | Set to true to make placeholder non-selectable, this will cause regions to set to first available when switching countries
removePlaceholder | no | false | boolean | Set to true to remove placeholder all together, this will autoselect first in list automatically


## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

## License
[MIT](https://choosealicense.com/licenses/mit/)
