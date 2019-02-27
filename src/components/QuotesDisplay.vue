<template>
    <div>
        <div class="container">
            <div @click="removeQuote(index)" v-for="(item, index) in quoteArray" :key="index" class="item">
                {{item}}
            </div>
        </div>
    </div>
</template>
<script>
import { quoteBus } from '../main.js';
export default {
    data: function(){
        return {
            quoteArray: [],
            quoteAmounts: 0
        }
    },
    created() {
        quoteBus.$on('addQuote', (quoteStatus) => {
            this.quoteArray.unshift(quoteStatus.quoteText);
            this.quoteAmounts = quoteStatus.quoteAmount;
        });
    },
    methods: {
        removeQuote(index){
            this.quoteArray.splice(index, 1);
            this.quoteAmounts--;
            quoteBus.$emit('removeQuote',{
                quoteAmount: this.quoteAmounts
            });
        }
    }
}
</script>
<style lang="scss" scoped>
@import url('https://fonts.googleapis.com/css?family=Dancing+Script');
.container{
    display: flex;
    flex-flow: row wrap;
    .item {
        min-height: 80px;
        margin: 2px;
        box-sizing: border-box;
        border: solid 1px black;
        box-shadow: 1px 1px 2px;
        flex: 0 0 32%;
        padding: 20px;
        font-family: 'Dancing Script', cursive;
    }
}
</style>