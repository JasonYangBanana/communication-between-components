<template>
  <div>
    <appQuotesCounter></appQuotesCounter>
    <appQuoteAdd></appQuoteAdd>
    <appQuotesDisplay></appQuotesDisplay>
    <div class="info">Click to remove the quote</div>
  </div>
</template>

<script>
import QuoteAdd from './components/QuoteAdd.vue';
import QuotesCounter from './components/QuotesCounter.vue';
import QuotesDisplay from './components/QuotesDisplay.vue';
export default {
  components: {
    appQuoteAdd: QuoteAdd,
    appQuotesCounter: QuotesCounter,
    appQuotesDisplay: QuotesDisplay
  }
}
</script>

<style lang="scss" scoped>
.info {
  background-color: lightgreen;
  color: darkblue;
  padding: 10px;
  text-align: center;
  border: solid 1px darkgreen;
  box-shadow: 1px 1px 7px;
}
</style>
