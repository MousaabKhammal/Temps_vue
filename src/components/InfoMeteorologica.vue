<template>
  <section class="container notification content is-large">
    <div class="column is-vcentered">
      <div class="column is-9">
        <div class="select">
          <select v-model="selectedCity">
            <option>Selecciona ciutat</option>
            <option v-for="ciutat in llistatCiutats" v-bind:key="ciutat" @click='itemClicked(ciutat)'>{{ ciutat }}</option>
          </select>
        </div>
        <div class="weather wrap">
          <div class="location-box">
            <div class="location">
              {{ ciutatActual.name }}
            </div>
          </div>
          <div class="weather-box">
            <div class="temp">
              {{ Math.round(ciutatActual.main.temp)  }}ºC
            </div>
            <div class="weather">
              {{ ciutatActual.weather[0].description }}
            </div>
          </div>
        </div>
      </div>

    </div>
  </section>
</template>

<script>

export default {
  name: "InfoMeteorologica",
  props: {
    llistatCiutats: [],
  },
  data: function () {
    return {
      selectedCity: null,
      ciutatActual: "barcelona"
    }
  },
  methods: {
    async getWeather(city) {
      const url = 'https://api.openweathermap.org/data/2.5/weather?q=' + city + '&units=metric&lang=ca&appid=644da4f2a1231c6611d2e2d8abb1fc90';

      try {
        var response = await fetch(url);
        var data = await response.json();

        this.ciutatActual = data;
      }
      catch(err) {
        console.log(err);
      }
    }
  },
  created: function () {
    this.selectedCity = this.llistatCiutats[0]
  },
  itemClicked: function(item) {
    this.getWeather(this.ciutatActual);
    this.onClick(item);
  },
  watch:{
    selectedCity(){
      this.getWeather(this.ciutatActual)
    }
  }
}
</script>

<style scoped>

</style>