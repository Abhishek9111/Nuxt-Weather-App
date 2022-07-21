<template>
  <v-container>
    <h1 class="display-1 text-xs-center">Weather App</h1>
    <v-layout>
      <v-flex xs12 class="mt-4">
        <v-card-text>Enter the name of the city </v-card-text>
      </v-flex>
      <v-form @submit.prevent="getWeatherInfo()">
        <v-flex xs12 class="mt-4">
          <v-text-field
            v-model="city"
            label="Enter City Name"
            solo
          ></v-text-field>
        </v-flex>
      </v-form>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  data: function() {
    return {
      city: 'London',
      weather: {}
    }
  },
  created() {},
  methods: {
    getWeatherInfo() {
      this.$axios
        .$get(
          `https://api.openweathermap.org/data/2.5/weather?q=${
            this.city
          }&appid=adaec12c8102f56ae4cbb886c5060f65`
        )
        .then(res => (this.weather = res))
    }
  }
}
</script>

<style></style>
