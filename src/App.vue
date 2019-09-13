<template>
  <div id="app">
    <div class="container">
      <BaseCurrency v-bind:rates="rates" v-bind:current_usd="current_usd" v-on:sharedCurrency="updateBaseCurrency"/>
      <Converted v-bind:current_usd='current_usd' v-bind:rates='rates' v-bind:showRates='showRates' v-on:delCurrency="delCurrency" />
      <AddCurrency v-on:newCurrency="addCurrency" v-bind:hiddenRates="hiddenRates"/>
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
      showRates: ['IDR','GBP','SGD'],
      rates: [],
      current_usd: 10
    }
  },

  methods: {
    updateBaseCurrency(usd) {
      this.current_usd = usd['usd'];
    },
    addCurrency(currency) {
      this.showRates.push(currency)
    },
    delCurrency(currency) {
      this.showRates = this.showRates.filter( which => which != currency)
    }
  },

  created () {
    axios.get('https://api.exchangeratesapi.io/latest')
    .then(res => this.rates = res.data['rates'])
    // .catch(err => console.log(err))
  },

  computed: {
    hiddenRates: function () {
      const filteredRates = [];
      for (var rate in this.rates) {
        filteredRates.push(rate)
      }
      for (var key of this.showRates) {
        return filteredRates.filter(which => which != key)
      }
      return filteredRates;
    }
  }
}
</script>

<style>
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
  /* font-family: 'Avenir', Helvetica, Arial, sans-serif; */
  font-family: "Roboto Slab", serif;
  font-weight:bold;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  width: 375px;
  height: 667px;
}
.container {

  padding:0px;
}
#app::-webkit-scrollbar {
    display: none;
}
</style>
