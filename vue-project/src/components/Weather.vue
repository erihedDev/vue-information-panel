<script>
import axios from 'axios'

const fetchData = `https://opendata-download-metanalys.smhi.se/api/category/mesan1g/version/2/geotype/point/lon/16.158/lat/58.5812/data.json`;
const minutes = 15 * 60;

async function fetchWeather(data) {
  let response = await axios.get(data);
  return response.data.timeSeries[0].parameters[1].values[0];
};

export default {
  data() {
    return {
      weather: {}
    };
  },

  async mounted() {
    this.weather = await fetchWeather(fetchData);

    setInterval(async () => {
      this.weather = await fetchWeather(fetchData);
    }, 1000 * minutes);

  }
};
</script>

<template>
  <div>
    <p>{{ weather }} °C</p>
  </div>
</template>