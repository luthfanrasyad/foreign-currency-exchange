<template>
  <div id="converted">
    <div class="converted-tab container-fluid">
      <div class="row" v-bind:key="item" v-for="item in this.showRates">
        <ConvertedValue v-bind:item="item" v-bind:current_usd='current_usd' v-bind:rates='rates' v-on:delCurrency="$emit('delCurrency',item)" />
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
    "current_usd","rates","showRates"

  ]
}
</script>


<style>
#converted {
  padding:5px;
}
</style>
