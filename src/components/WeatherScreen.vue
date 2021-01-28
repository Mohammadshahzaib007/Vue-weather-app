<template>
  <v-container class="mt-6">
    <v-row justify="center">
      <v-col cols="6">
        <v-card class="pa-6 center" min-height="37.5rem">
          <search-bar @getWeather="getWeather" :isLoading="isLoading" />
          <results
            :weatherDetails="weatherDetails"
            v-if="weatherDetails.temp && !isLoading && !error"
          />
          <h4 v-else-if="error" class="text-center text-uppercase">
            {{ error }}
          </h4>
          <v-col v-else-if="isLoading" cols="12" id="progres">
            <v-progress-circular
              indeterminate
              color="amber"
            ></v-progress-circular>
          </v-col>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import SearchBar from "./SearchBar.vue";
import Results from "./Results.vue";

export default {
  components: { SearchBar, Results },
  data() {
    return {
      weatherDetails: {
        cityName: "",
        country: "",
        weatherType: "",
        temp: null,
        maxTemp: null,
        minTemp: null,
        humidity: null,
        windSpeed: null,
      },
      isLoading: false,
      error: "",
    };
  },
  methods: {
    getWeather(query) {
      const apiKey = "398d98ca670466934423306cfc3f03d5";
      this.isLoading = true;
      fetch(
        `http://api.openweathermap.org/data/2.5/weather?q=${query}&units=metric&appid=${apiKey}`
      )
        .then((response) => {
          return response.json();
        })
        .then((data) => {
          if (data.cod === "404") {
            this.isLoading = false;
            this.error = data.message;
            return;
          }
          this.error = "";
          this.isLoading = false;
          this.weatherDetails.cityName = data.name;
          this.weatherDetails.country = data.sys.country;
          this.weatherDetails.weatherType = data.weather[0].main;
          this.weatherDetails.temp = data.main.temp;
          this.weatherDetails.maxTemp = data.main.temp_max;
          this.weatherDetails.minTemp = data.main.temp_min;
          this.weatherDetails.humidity = data.main.humidity;
          this.weatherDetails.windSpeed = data.wind.speed;
        })
        .catch(() => {
          this.isLoading = false;
          this.error = "There is something wrong Please try again later...";
        });
    },
  },
};
</script>

<style scoped>
#progres {
  display: flex;
  justify-content: center;
}
</style>