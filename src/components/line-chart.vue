<script>
import { Line } from "vue-chartjs";
import "chartjs-plugin-streaming";
export default {
  extends: Line,
  props: ["live"],
  data() {
    return {
      chartData: {
        datasets: [
          {
            label: "Helo",
            backgroundColor: "#5DA3FA30",
            borderColor: "#5DA3FA",
            borderWidth: 2,
            id: "halo",
            lineTension: 0.05,
            fill: true,
            pointRadius: 2.5,
            data: [],
          },
          {
            label: "Helo",
            backgroundColor: "#4DD63730",
            borderColor: "#4DD637",
            borderWidth: 2,
            id: "halo1",
            lineTension: 0.05,
            fill: true,
            pointRadius: 2.5,
            data: [],
          },
        ],
      },
      options: {
        legend: {
          display: true,
          position: "bottom",
          labels: {
            boxWidth: 15,
          },
        },
        response: true,
        maintainAspectRatio: false,
        scales: {
          yAxes: [
            {
              scaleLabel: {
                display: true,
                labelString: "Speed",
              },
              ticks: {
                beginAtZero: true,
              },
            },
          ],
          xAxes: [
            {
              type: "realtime",
              time: {
                tooltipFormat: "HH:mm:ss A",
                displayFormats: {
                  second: "s[s]",
                  minute: "s[s]",
                },
              },
              realtime: {
                duration: 60000,
                refresh: 1000,
                delay: 0,
                pause: false,
                // frameRate: 60,
                ttl: undefined,
                onRefresh: this.onRefreshChart,
              },
            },
          ],
        },
      },
    };
  },
  watch: {
    live(val) {
      this.$data._chart.options.scales.xAxes[0].realtime.pause = !val;
    },
  },
  mounted() {
    this.renderChart(this.chartData, this.options);
  },
  methods: {
    onRefreshChart(chart) {
      chart.data.datasets.forEach((dataset) => {
        let val = Math.floor(Math.random() * 10);
        dataset.data.push({
          x: Date.now(),
          y: val,
        });
        dataset.label = "Helo " + val;
        chart.update();
      });
    },
  },
};
</script>
