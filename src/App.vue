<template>
    <div class="container">
        <app-header v-bind:maxQuotes="maxQuotes" v-bind:quoteCount="quotes.length"></app-header>
        <app-new-quote v-on:quoteAdded="newQuote"></app-new-quote>
        <app-quote-grid v-bind:quotes="quotes" v-on:quoteDeleted="deleteQuote"></app-quote-grid>
        <div class="row">
            <div class="col-sm-12 text-center">
                <div class="alert alert-info">
                    Info: Click on a Quote to delete it!
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import QuoteGrid from './components/QuoteGrid.vue';
    import NewQuote from './components/NewQuote.vue';
    import Header from './components/Header.vue';

    export default {
        data: function() {
            return {
                quotes: [
                    'May the force be with you.',
                    'I have the high ground.',
                    'I am your father.',
                    'Every thing is going as planned.',
                    'I find your lack of faith disturbing.',
                    'I have a bad feeling about this.',
                    'You were the Chosen One! You were supposed to destroy the Sith, not join them. You were supposed to bring balance to the force, not leave it in darkness.',
                    'Leia - I love you.',
                    'Han - I know.'
                ],
                maxQuotes: 10
            }
        },
        methods: {
            newQuote(quote) {
                if (this.quotes.length >=this.maxQuotes) {
                    return alert('Please delete some Quote first!');
                }
                this.quotes.push(quote);
            },
            deleteQuote(index) {
                this.quotes.splice(index, 1);
            }
        },
        components: {
            appQuoteGrid: QuoteGrid,
            appNewQuote: NewQuote,
            appHeader: Header
        }
    }
</script>

<style>
</style>
