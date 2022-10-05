<script setup>

</script>
<script>
import DatePicker from './components/DatePicker.vue';

export default {
  components: {
    DatePicker
  },

  data() {
    return {
      range: null
    }
  }
}

</script>

<template>
  <div id="app">
    <DatePicker @get-range="(range) => this.range = range"></DatePicker>

    <div v-if="range != null">
      The date range is: {{range}}
    </div>

    
  </div>
</template>

<style scoped>

</style>
