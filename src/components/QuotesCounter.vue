<template>
    <div>
        <h3>Quote Added</h3>
        <!-- <button @click="currentQuoteAmounts++">click</button> -->
        <div class="bar">
            <div class="text">{{ currentQuoteAmounts }}/10</div>
            <div class="currentQuoteAmounts" :style="barLength"></div>
        </div>
        <!-- <button @click="currentQuoteAmounts = 0">reset</button> -->
    </div>
</template>
<script>
import { quoteBus } from '../main.js';
export default {
    data: function(){
        return {
            currentQuoteAmounts: 0
        }
    },
    created() {
        quoteBus.$on('addQuote', (quoteStatus) => {
            this.currentQuoteAmounts = quoteStatus.quoteAmount;
        });
        quoteBus.$on('removeQuote', (quoteStatus) => {
            this.currentQuoteAmounts = quoteStatus.quoteAmount;
        });
    },
    computed: {
        barLength: function () {
            return {
                width: `${this.currentQuoteAmounts / 10 * 100}%`
            };
        }
    }
}
</script>
<style lang="scss" scoped>
    .bar {
        position: relative;
        background-color: lightgray;
        width: 90vw;
        margin: 0 auto;
        text-align: center;
        .text {
            position: relative;
            z-index: 1;
        }
        .currentQuoteAmounts{
            position: absolute;
            top: 0;
            background-color: lightblue;
            transition: width 0.2s ease-in-out;
            height: 100%;
        }
    }
</style>