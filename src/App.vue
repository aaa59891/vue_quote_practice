<template>
    <div class="container">
        <app-progress :max="maxQuotes" :current="quotes.length"></app-progress>
        <app-add></app-add>
        <app-quote-grid :quotes="quotes"></app-quote-grid>
        <div class="row">
            <div class="col-sm-12 text-center">
                <div class="alert alert-info">Info: Click on a quote to delete it!</div>
            </div>
        </div>
    </div>
</template>

<script>
    import Progress from './components/Progress.vue';
    import Add from './components/Add.vue';
    import QuoteGrid from './components/QuoteGrid.vue';
    import { QuoteEvent } from './main.js';
    import { deleteQuote, addQuote } from './const/QuoteEvent.js';
import QuoteVue from './components/Quote.vue';
    export default {
        data: function(){
            return {
                quotes: [
                    'first quote',
                    'second quote'
                ],
                maxQuotes: 10,
            };
        },
        components:{
            'app-progress': Progress,
            'app-add': Add,
            'app-quote-grid': QuoteGrid
        },
        created(){
            QuoteEvent.$on(deleteQuote, (index) => {
                this.quotes.splice(index, 1);
            });
            QuoteEvent.$on(addQuote, (quote) => {
                if (this.quotes.length == this.maxQuotes){
                    alert('The quotes can not exceed more than 10.')
                    return
                }
                this.quotes.push(quote);
            });
        }
    }
</script>

<style>
</style>