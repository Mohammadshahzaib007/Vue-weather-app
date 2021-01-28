<template>
  <v-app>
    <!-- <v-navigation-drawer app> -->
    <!-- -->
    <!-- </v-navigation-drawer> -->

    <navigation />

    <!-- Sizes your content based upon application components -->
    <v-main>
      <weather-screen />
    </v-main>

    <v-footer app>
      <!-- -->
    </v-footer>
  </v-app>
</template>

<script>
import Navigation from "./Navigation";
import WeatherScreen from "./WeatherScreen.vue";

export default {
  components: {
    Navigation,
    WeatherScreen,
  },
};
</script>

<style scoped>
</style>