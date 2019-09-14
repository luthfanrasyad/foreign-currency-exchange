<template>
  <div id="converted">
    <div class="converted-tab container-fluid">
      <div class="row" v-bind:key="rate" v-for="rate in this.showRates"> <!--Call the ConvertedValue component for every rate in the showRates list -->
        <ConvertedValue v-bind:rate="rate" v-bind:currentUSD='currentUSD' v-bind:allRates='allRates' v-on:delCurrency="$emit('delCurrency',rate)" />
      </div>
    </div>
  </div>
</template>

<script>


import ConvertedValue from '../components/ConvertedValue.vue'

export default {

  name: 'Converted',
  components: {
    ConvertedValue
  },
  props: [
    "currentUSD","allRates","showRates"

  ]
}
</script>
<style lang="scss">
#converted {
  padding:5px;
}
</style>
