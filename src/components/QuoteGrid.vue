<template>
    <div class="row">
        <app-quote v-for="(quote, index) in quotes" @click.native="deleteQuote(index)">
            {{ quote }}
        </app-quote>
    </div>
</template>

<script>
    import Quote from './Quote.vue';
    import { QuoteEvent } from '../main.js';
    import { deleteQuote } from '../const/QuoteEvent.js';
    export default {
        props:{
            quotes: Array
        },
        methods: {
            deleteQuote(index){
                QuoteEvent.$emit(deleteQuote, index);
            }
        },
        components: {
            'app-quote': Quote
        }
    }
</script>

<style scoped>
</style>