<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <v-subheader class="text-h4">Live Chart</v-subheader>
    </v-app-bar>

    <v-main>
      <chart />
    </v-main>
  </v-app>
</template>

<script>
import Chart from "./components/chart.vue";

export default {
  name: "App",

  components: {
    Chart,
  },

  data: () => ({
    //
  }),
};
</script>
