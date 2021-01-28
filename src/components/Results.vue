<template>
  <v-row justify="center">
    <v-col cols="12">
      <h4 class="text-center text-uppercase">{{ weatherDetails.cityName }}</h4>
      <p class="text-center caption">{{ weatherDetails.country }}</p>
    </v-col>

    <v-col cols="6" align-self="center">
      <v-card
        min-width="9.375rem"
        min-height="6.25rem"
        color="rgba(0, 0, 0, .8)"
        id="card"
      >
        <h1 class="mt-0">{{ temp }}&deg;c</h1>
        <p class="overline mt-0" style="color: white">
          {{ weatherDetails.weatherType }}
        </p>
      </v-card>
    </v-col>

    <v-col cols="12" class="mt-4">
      <h4 class="text-center text-uppercase">Weather Details</h4>
    </v-col>
    <v-col cols="12">
      <v-card color="rgba(0, 0, 0, .8)">
        <v-row>
          <v-col cols="6" class="pa-4"
            ><h1 class="text-center subtitle-1">Max Temprature</h1></v-col
          >
          <v-col cols="6" class="pa-4"
            ><h1 class="text-center headline">{{ maxTemp }}&deg;c</h1></v-col
          >

          <v-col cols="6" class="pa-4"
            ><h1 class="text-center subtitle-1">Min Temprature</h1></v-col
          >
          <v-col cols="6" class="pa-4"
            ><h1 class="text-center headline">{{ minTemp }}&deg;c</h1></v-col
          >

          <v-col cols="6" class="pa-4"
            ><h1 class="text-center subtitle-1">Humidity</h1></v-col
          >
          <v-col cols="6" class="pa-4"
            ><h1 class="text-center headline">
              {{ weatherDetails.humidity }}%
            </h1></v-col
          >

          <v-col cols="6" class="pa-4"
            ><h1 class="text-center subtitle-1">Wind Speed</h1></v-col
          >
          <v-col cols="6" class="pa-4"
            ><h1 class="text-center headline">
              {{ weatherDetails.windSpeed }} km/h
            </h1></v-col
          >
        </v-row>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  props: ["weatherDetails"],
  computed: {
    temp() {
      return Math.floor(this.weatherDetails.temp);
    },
    maxTemp() {
      return Math.floor(this.weatherDetails.maxTemp);
    },
    minTemp() {
      return Math.floor(this.weatherDetails.minTemp);
    },
  },
};
</script>

<style scoped>
#card {
  display: flex;
  align-items: center;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
h1 {
  color: white;
}
</style>