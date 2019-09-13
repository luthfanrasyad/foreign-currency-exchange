<template>
  <div id="base_currency">
    <div class="container-fluid">
      <div class="valuation-title row">
        <p><i>USD - United States Dollars</i></p>
      </div>
      <div class=" valuation row justify-content-between">
        <p><b>USD</b></p>
        <form class="currency_input">
          <input type='number' min='0' v-on:input="$emit('sharedCurrency',{'usd':base_currency})" v-model='base_currency' name="base_currency" place="USD Base Currency">
        </form>
      </div>

    </div>
  </div>
</template>

<script>
export default {
  name: 'BaseCurrency',
  props: [
    "rates",
    "current_usd"
  ],
  data() {
    return {
      base_currency: this.current_usd
    }
  }
}
</script>

<style>
#base_currency {
  padding: 15px 15px 5px 15px;
  margin-bottom: 5px;
  border-bottom:2px solid black;
}
.currency_input {
  width:80%;
}
.currency_input input {
  text-align: right;
  height:100%;
  vertical-align: middle;
  width:100%;
  font-weight: bold;
  border:none;
}
.valuation-title {
  margin-bottom: 0px;
}
.valuation p {
  margin:auto;
  margin-left:0px
}
.valuation {
  margin-bottom: 7px;
}
</style>
