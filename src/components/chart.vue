<template>
  <v-card class="ma-5">
    <v-switch v-model="live" class="ma-4" label="Live"></v-switch>
    <line-chart :live="live"></line-chart>
  </v-card>
</template>

<script>
import LineChart from "./line-chart.vue";
export default {
  components: {
    LineChart,
  },
  data() {
    return {
      live: true,
    };
  },
};
</script>

<style></style>
