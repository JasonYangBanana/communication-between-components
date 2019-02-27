<template>
  <div>
    <appQuotesCounter></appQuotesCounter>
    <appQuoteAdd></appQuoteAdd>
    <appQuotesDisplay></appQuotesDisplay>
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

<style lang="scss">

</style>
