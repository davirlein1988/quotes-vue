<template>
    <div class="container">
        <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
        <app-new-quote @quoteAdded="newQuote"></app-new-quote>
        <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
        <div class="row">
            <div class="col-sm-12 text-center">
                <div class="alert alert-info">Info: Click on a quote to delete it!</div>
            </div>
        </div>
    </div>
</template>

<script>
import QuoteGrid from './components/QuoteGrid.vue'
import NewQuote from './components/NewQuote.vue'
import Header from './components/Header.vue'
    export default {
        data: function () {
            return {
                quotes: [
                    'Just a simple quote to see some data'
                ],
                maxQuotes: 10
            }
        },
        methods: {
            newQuote(quote){
                if(this.quotes.length >= this.maxQuotes) {
                    return alert("Please, delete some quotes...")
                }
                this.quotes.unshift(quote)
            },
            deleteQuote(index){
            this.quotes.splice(index, 1)
            }
        },
        components: {
            AppQuoteGrid: QuoteGrid,
            AppNewQuote: NewQuote,
            AppHeader: Header
        }
    }
</script>

<style>
</style>
