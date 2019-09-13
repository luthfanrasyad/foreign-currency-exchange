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
.btn-secondary.focus, .btn-secondary:focus {
    box-shadow: 0 0 0 0rem rgba(108,117,125,.5);
}
.btn-secondary:hover {
  background-color:white;
  border-color:black;
  color:black;
}

.dropup button{
  width:100%;
  margin-left: 0px;
  border-radius: 0px !important;

}
.btn-secondary {
    color: white;
    background-color:#4d2a86;
    border-color: black;
    border:2px solid black;
}
</style>
