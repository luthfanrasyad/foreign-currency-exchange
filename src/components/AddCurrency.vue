<template>
  <div id="add-currency">
    <div class="add-currency-tab container-fluid">
      <div class="dropup">
        <button class="btn btn-secondary " type="button" id="dropdownMenuButton" data-toggle="dropdown" aria-haspopup="true" aria-expanded="true">
          <b>Add More Currencies</b>
        </button>
        <div class="dropdown-menu" aria-labelledby="dropdownMenuButton">
          <div v-for="rate in hiddenRates">
            <a class="dropdown-item" v-on:click="$emit('newCurrency',rate)" > {{rate}}</a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>


export default {

  name: 'AddCurrency',
  props: [
    "current_usd","rates","showRates","hiddenRates"

  ]
}
</script>


<style>
#add-currency {

}
.add-currency-tab {
  padding: 0px 5px;
  margin-bottom:5px;
}

.dropup button{
  width:100%;
  margin-left: 0px;
  border-radius: 0px !important;

}
.btn-secondary {
    color: black;
    background-color: white;
    border-color: black;
    border:2px solid black;
}
</style>
