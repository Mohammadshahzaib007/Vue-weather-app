<template>
  <v-row justify="center" align="center">
    <v-col cols="8">
      <v-text-field
        class="pt-5"
        label="Enter City Name"
        outlined
        shaped
        append-icon="mdi-magnify"
        v-model.trim="enteredText"
      ></v-text-field>
    </v-col>

    <v-col cols="4">
      <v-btn
        color="primary"
        @click="$emit('getWeather', enteredText)"
        :loading="isLoading"
      >
        <v-icon left>mdi-magnify</v-icon>
        Search
      </v-btn>
    </v-col>
  </v-row>
</template>


<script>
export default {
  emits: ["getWeather"],
  props: ["isLoading"],
  data() {
    return {
      enteredText: "",
    };
  },
};
</script>