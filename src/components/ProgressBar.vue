<template>
  <div class="container">
    <div class="col-12 row justify-content-md-center">
      <div class="col-8">
        <h1>{{ counter }}</h1>
        <div class="progress">
          <div class="progress-bar" role="progressbar" :style="width()" aria-valuemin="0" aria-valuemax="100">{{ counter*10 }}%</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { eventBus } from '../main'
export default {
  name: 'HelloWorld',
  data: function() {
    return {
      counter: 0
    }
  },
  created() {
    eventBus.$on("counterUpdated",(counter) => {
      this.counter = counter;
    });
  },
  methods: {
    width: function() {
      return 'width: ' + this.counter*10 + '%';
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
