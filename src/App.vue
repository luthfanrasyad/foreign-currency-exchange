<template>
  <div id="app">
    <div class="container">
      <BaseCurrency v-bind:currentUSD="currentUSD" v-on:updateBaseCurrency="updateBaseCurrency"/>
      <Converted v-bind:currentUSD='currentUSD' v-bind:allRates='allRates' v-bind:showRates='showRates' v-on:delCurrency="delCurrency" />
      <AddCurrency v-on:addCurrency="addCurrency" v-bind:hiddenRates="hiddenRates"/>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import BaseCurrency from './components/BaseCurrency.vue'
import Converted from './components/Converted.vue'
import AddCurrency from './components/AddCurrency.vue'

export default {
  name: 'app',
  components: {
    BaseCurrency,
    Converted,
    AddCurrency
  },
  data() {
    return {
      allowedRates: ['CHF','USD','CAD','IDR','GBP','SGD','INR','MYR','JPY','KRW','AUD','HKD','CNY'],
      showRates: ['IDR','GBP','SGD'],
      allRates: [],
      currentUSD: 10
    }
  },

  methods: {
    //Update the base currency everytime the value is changed in the input field located in the BaseCurrency component
    updateBaseCurrency(usd) {
      this.currentUSD = usd['usd'];
    },
    //Add currency to the list of rates to show.
    addCurrency(currency) {
      this.showRates.push(currency)
    },
    //Remove currency from the list to show based on the name that was passed from the ConvertedValue component
    delCurrency(currency) {
      this.showRates = this.showRates.filter( which => which != currency)
    }
  },

  //To retreive the data from the API
  created () {
    axios.get('https://api.exchangeratesapi.io/latest')
    .then(res => this.allRates = res.data['rates'])
    .catch(err => console.log(err))
  },

  //To define which rates are not being shown based on the allowedRates and showRates lists.
  //This prevents any duplicates from being able to be shown on the application.
  computed: {
    hiddenRates: function () {
      let filteredRates = [];
      for (var rate in this.allRates) {
        if (this.allowedRates.includes(rate)){
            filteredRates.push(rate)
        }
      }
      for (var key of this.showRates) {
        filteredRates = filteredRates.filter(which => which != key)
      }
      return filteredRates;
    }
  }
}
</script>

<style lang='scss'>
html, body {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100%;
}
#app {
  overflow-y: scroll;
  width:500px;
  border: 2px solid black;
  font-family: "Roboto Slab", serif;
  font-weight:500;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  width: 375px;
  height: 667px;

  .container {
    padding:0px;
  }
}
#app::-webkit-scrollbar {
    display: none;
}
</style>
