<template>
  <div id="base_currency">
    <div class="container-fluid">
      <div class="valuation-title row">
        <p><i>USD - United States Dollars</i></p>
      </div>
      <div class=" valuation row justify-content-between">
        <p><b>USD</b></p>
        <form class="currency_input">
          <input type='number' min='0' v-on:input="$emit('updateBaseCurrency',{'usd':baseCurrency})" v-model='baseCurrency' name="baseCurrency" placeholder="Amount">
        </form>
      </div>

    </div>
  </div>
</template>

<script>
export default {
  name: 'BaseCurrency',
  props: [
    "currentUSD"
  ],
  data() {
    return {
      baseCurrency: this.currentUSD
    }
  }
}
</script>

<style lang="scss">
#base_currency {
  padding: 15px 15px 5px 15px;
  margin-bottom: 5px;
  border-bottom:2px solid black;
  background-color: #4d2a86;
  color:white;

  .valuation-title {
    margin-bottom: 0px;
  }

  .valuation {
    margin-bottom: 7px;
    font-size:26px;
    p {
     margin:auto;
     margin-left:0px
    }

  }
  .currency_input {
    width:80%;
    input {
     text-align: right;
     height:100%;
     vertical-align: middle;
     width:100%;
     font-weight: bold;
     border:none;
     background-color: #4d2a86;
     color:white;
   }
    input:focus {
      outline:none;
    }
  }
}

</style>
