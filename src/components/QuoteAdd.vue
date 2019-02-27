<template>
    <div class="container">
        <h4 class="text">Quote</h4>
        <textarea v-model="quoteText" name="Quote" cols="70" rows="10"></textarea>
        <button @click="addQuote">Add Quote</button>
    </div>
</template>
<script>
import { quoteBus } from '../main.js';
export default {
    data: function(){
        return {
            quoteText: '',
            quoteAmount: 0
        };
    },
    methods:{
        addQuote(){
            if(this.quoteAmount >= 10){
                return alert('No more quotes');
            }
            this.quoteAmount++;
            quoteBus.$emit('addQuote', {
                quoteText: this.quoteText, 
                quoteAmount: this.quoteAmount
            });
            this.quoteText = '';
        }
    }
}
</script>
<style lang="scss" scoped>
    .container {
        text-align: center;
    }
</style>