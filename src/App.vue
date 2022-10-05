<script setup>

</script>
<script>
import MyDatePicker from './components/MyDatePicker.vue';
import Chart from './components/Chart.vue';

export default {
  components: {
    MyDatePicker, BarChart: Chart
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
    <MyDatePicker @get-range="(range) => this.range = range"></MyDatePicker>

    <div v-if="range != null">
      <Chart :range="range">

      </Chart>
    </div>


  </div>
</template>

<style scoped>

</style>
