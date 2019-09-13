<template>
  <div id="converted-value">
    <div class="d-flex  converted-value-tab container-fluid">
      <div class="col-10">
        <div class="row updated-value">
          <h5>{{this.item}}</h5>
          <h5 class="ml-auto"><b>{{this.convertedValue}}</b></h5>
        </div>
        <div class="row original-currency" >
          <p><i>{{this.item}}</i></p>
        </div>
        <div class="row original-value">
          <p><i>1 USD = {{this.item}} {{this.rates[this.item]}}</i></p>
        </div>
      </div>

      <div class="del-button col-2">
          <button class="btn" v-on:click="$emit('delCurrency',item)">  <font-awesome-icon icon="trash" /></button>
      </div>
    </div>
  </div>
</template>

<script>


export default {

  name: 'ConvertedValue',
  props: [
    "item",
    "current_usd",
    "rates"
  ],
  computed: {
    convertedValue: function () {
      return (this.current_usd * this.rates[this.item]).toFixed(2)
    }
  }
}
</script>

<style>
#converted-value {
  border: 2px solid black;
  padding:0px 5px;
  width:100%;
  margin-bottom:5px;

}
.converted-value-tab {

  padding: 5px;
  padding-right:0px;
}
.del-button {
  padding:0px;
}

.del-button button {
  position:absolute;
  right:0;
  bottom:0;
  padding:0px;
  margin:0px;
  height:45%;
  width:40%;
}
.del-button img {
  position: absolute;
  bottom:0px;
  right: 0px;
}
.btn {
  background-color: none;
}
.updated-value {
  padding-right:10px;
}
.original-value p , .original-currency p {
  margin-bottom:0px;
}
</style>
