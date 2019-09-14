<template>
  <div id="converted-value">
    <div class="d-flex  converted-value-tab container-fluid">
      <div class="col-10">
        <div class="row updated-value">
          <h5><b>{{this.rate}}</b></h5>
          <h5 class="ml-auto"><b>{{this.convertedValue}}</b></h5>
        </div>
        <div class="row original-currency" >
          <p><b><i>{{this.rate}} - {{this.currencyName[this.rate]}}</i></b></p>
        </div>
        <div class="row original-value">
          <p><i>1 USD = {{this.rate}} {{this.allRates[this.rate]}}</i></p>
        </div>
      </div>
      <div class="del-button col-2">
          <button class="btn" v-on:click="$emit('delCurrency',rate)">  <font-awesome-icon icon="trash" /></button>
      </div>
    </div>
  </div>
</template>

<script>
export default {

  name: 'ConvertedValue',
  props: [
    "rate",
    "currentUSD",
    "allRates"
  ],
  data() {
    return {
      currencyName: {
        'IDR' : 'Indonesian Rupiah',
        'GBP' : 'British Pound',
        'SGD' : 'Singapore Dollar',
        'CAD' : 'Canadian Dollar',
        'HKD' : 'Hong Kong Dollar',
        'ISK' : 'Islandic Krona',
        'PHP' : 'Phillipine Peso',
        'DKK' : 'Danish Krone',
        'HUF' : 'Hungarian Forint',
        'CZK' : 'Czech Koruna',
        'AUD' : 'Australian Dollar',
        'RON' : 'Romanian Leu',
        'SEK' : 'Swedish Krona',
        'INR' : 'Indian Rupee',
        'BRL' : 'Brazilian Real',
        'RUB' : 'Russian Ruble',
        'HRK' : 'Croatian Kuna',
        'JPY' : 'Japanese Yen',
        'THB' : 'Thai Baht',
        'CHF' : 'Swiss Franc',
        'PLN' : 'Polish Zloti',
        'BGN' : 'Bulgarian Lev',
        'TRY' : 'Turkish Lira',
        'CNY' : 'Chinese Yuan',
        'NOK' : 'Norwegian Krone',
        'NZD' : 'New Zealand Dollar',
        'ZAR' : 'South African Rand',
        'USD' : 'United States Dollar',
        'MXN' : 'Mexican Peso',
        'ILS' : 'Israeli New Shekel',
        'KRW' : 'South Korean Won',
        'MYR' : 'Malaysian Ringgit'
      }
    }
  },
  // To calculate the converted rate based on the amount of base currency (USD) multiplied by the rate.
  computed: {
    convertedValue: function () {
      return (this.currentUSD * this.allRates[this.rate]).toFixed(2)
    }
  }
}
</script>

<style lang="scss">
#converted-value {
  border: 2px solid black;
  padding:0px 5px;
  width:100%;
  margin-bottom:5px;
  .converted-value-tab {
    padding: 5px;
    padding-right:0px;
    .updated-value {
      padding-right:10px;
    }
    .original-value p , .original-currency p {
      margin-bottom:0px;
    }
    .del-button {
      padding:0px;
      button {
        position:absolute;
        right:0;
        bottom:0;
        padding:0px;
        margin:0px;
        height:45%;
        width:40%;
      }
      img {
       position: absolute;
       bottom:0px;
       right: 0px;
     }
    }
  }
}
</style>
