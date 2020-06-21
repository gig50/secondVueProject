<template>
  <div class="container">
    <app-progress-bar :maxQuotes="maxquotes" :quoteCount="quotes.length"></app-progress-bar>
    <app-new-quote @quoteAdded="newQuote"></app-new-quote>
    <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
    <div class="row">
      <div class="col-sm-12 text-center">
        <div class="alert alert-info">Info: Click on a Quote to delete it!</div>
      </div>
    </div>
  </div>
</template>

<script>
import QuoteGrid from "./components/QuoteGrid.vue";
import NewQuote from "./components/NewQuote.vue";
import ProgressBar from "./components/Header.vue";
export default {
  data: function() {
    return {
      quotes: ["This is just a qoute to see if it works"],
      maxquotes: 10
    };
  },
  components: {
    appQuoteGrid: QuoteGrid,
    appNewQuote: NewQuote,
    appProgressBar: ProgressBar
  },
  methods: {
    newQuote(data) {
        if(this.quotes.length >= this.maxquotes){
           return alert("Please delete quotes first!")
        }
      this.quotes.push(data);
    },
    deleteQuote(data) {
      this.quotes.splice(data, 1);
    }
  }
};
</script>

<style>
</style>
