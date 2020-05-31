<template>
  <div class="container">
    <div class="row">
      <div class="col-md-3" v-for="quote in quotes" :key="quote.id">
        <quote :quoteProp=quote></quote>
      </div>
    </div>
  </div>
</template>

<script>
import { eventBus } from '../main'
import quote from './Quote'
export default {
  data: function() {
    return {
      idCounter: 2,
      counter: 2,
      quotes: [
        {
          'id': 1,
          'content': "Hola!"
        },
        {
          'id': 2,
          'content': "Chao!"
        }
      ]
    }
  },
  created() {
    eventBus.$on("addQuote", (text) => {
      if(this.counter < 10){
        this.quotes.push({'id': this.idCounter += 1, 'content': text});
        this.counter += 1;
        eventBus.$emit("quoteProcessed","ok");
        eventBus.$emit("counterUpdated",this.counter);
      }
      else{
        eventBus.$emit("quoteProcessed","error");
      }
    });
    eventBus.$on("removeQuote",(id) => {
      var newQuotes = new Array();
      var newCounter = 0;
      for(var i = 0; i < this.quotes.length; i++){
        var quote = this.quotes[i];
        if(quote.id != id){
          newQuotes.push(quote);
          newCounter += 1;
        }
      }
      this.quotes = newQuotes;
      this.counter = newCounter;
      eventBus.$emit("counterUpdated",this.counter);

    });
    eventBus.$emit("counterUpdated",this.counter);
  },
  components: {
    quote
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

</style>
