<template>
  <div class="col-md-12">
    <h1>{{this.quoteProp.content}}</h1>
    <button @click="removeQuote">Remove!</button>
  </div>
</template>

<script>
import { eventBus } from '../main'
export default {
  props: {
    quoteProp: Object
  },
  methods: {
    removeQuote: function() {
      eventBus.$emit("removeQuote",this.quoteProp.id)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
</style>
