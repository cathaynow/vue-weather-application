<template>
  <div class="weather-wrapper">
    <ContentHeader />
    <CitySelector @selectCity="selectCity" />
    <weatherList :weatherList="weatherList" :weather="weather" />
  </div>
</template>

<script>
import weatherMixin from "@/mixins/weatherMixin";
import ContentHeader from "./ContentHeader"; //안내문구
import CitySelector from "./CitySelector"; //도시선택
import weatherList from "./WeatherList";

export default {
  name: "WeatherContent",
  components: {
    ContentHeader,
    CitySelector,
    weatherList,
  },
  mixins: [weatherMixin],
  data() {
    return {
      weatherList: [],
    };
  },
  methods: {
    async selectCity(city) {
      if (city.selected) {
        const weather = await this.getWeatherInfo(city);
        //console.log(weather, "wether");
        this.weatherList.push(weather);
      } else {
        const index = this.weatherList.findIndex(
          (weather) => weather.code === city.code
        );
        //console.log(index);
        this.weatherList.splice(index, 1);
      }
      //console.log(city, "parent received");
    },
  },
};
</script>

<style scoped></style>
