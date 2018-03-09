<template>
    <div class="row">
        <form>
            <div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3 form-group">
                <textarea class="form-control" name="" id="" cols="30" rows="10" v-model="quote"></textarea>
            </div>
            <div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3 form-group text-center">
                <button class="btn btn-primary" @click.prevent="addQuote">Add</button>
            </div>
        </form>
    </div>
</template>

<script>
    import { QuoteEvent } from '../main.js';
    import { addQuote } from '../const/QuoteEvent.js';
    export default {
        data: function () {
            return {
                quote: ''
            };
        },
        methods: {
            addQuote() {
                QuoteEvent.$emit(addQuote, this.quote);
                this.quote = '';
            }
        }
    }
</script>

<style scoped>
</style>