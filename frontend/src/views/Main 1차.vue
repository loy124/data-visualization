<template>
  <div>
    <reactive-bar-chart
      style="width:40vw;"
      v-if="chartData"
      :chart-data="chartData"
    ></reactive-bar-chart>
  </div>
</template>

<script>
import ReactiveBarChart from "../components/ReactiveBarChart.js";
export default {
  name: "App",
  components: {
    ReactiveBarChart,
  },
  data() {
    return {
      chartData: null,
    };
  },
  methods: {
    generateData() {
      let newArray = [];
      let newArray2 = [];
      for (let i = 0; i < 10; i++) {
        let randomValue = Math.floor(Math.random() * 10);
        newArray.push(randomValue);
      }

      for (let i = 0; i < 10; i++) {
        let randomValue = Math.floor(Math.random() * 10);
        newArray2.push(randomValue);
      }

      this.chartData = {
        labels: ["Red", "Blue", "Yellow", "Green", "Purple", "Orange"],
        datasets: [
          {
            label: "Data One",
            backgroundColor: "#f87979",
            data: newArray,
            fill: false,
          },
          {
            label: "Data One",
            backgroundColor: "#f87979",
            data: newArray2,
            fill: false,
          },
        ],
      };
    },

  },
  async mounted() {
    setInterval(this.generateData, 2000);
  },
};
</script>

<style></style>
