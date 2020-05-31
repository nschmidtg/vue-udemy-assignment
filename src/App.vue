<template>
  <div id="app">
    <progressBar counter="counter"/>
    <quoteForm/>
    <quoteGrid quotes="quotes"/>
  </div>
</template>

<script>
import progressBar from './components/ProgressBar.vue'
import quoteForm from './components/QuoteForm.vue'
import quoteGrid from './components/QuoteGrid.vue'

export default {
  name: 'App',
  data: function() {
    return {
    }
  },
  components: {
    progressBar,
    quoteForm,
    quoteGrid
  }
}
</script>

<style>

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
