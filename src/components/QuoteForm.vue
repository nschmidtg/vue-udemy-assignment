<template>
  <div class="content">
    <input v-model="text" type="text">
    <button @click="addQuote">Agregar Quote</button>
  </div>
</template>

<script>
import { eventBus } from '../main'
export default {
  name: 'HelloWorld',
  data: function() {
    return {
      text: ""
    }
  },
  methods: {
    addQuote: function () {
      eventBus.$emit("addQuote",this.text);
    }
  },
  created() {
    eventBus.$on("quoteProcessed",(status) => {
      if(status === "error"){
        alert("No caben más quotes")
      }
      else{
        this.text = "";
      }
    })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
