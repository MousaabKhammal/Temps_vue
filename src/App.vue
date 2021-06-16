<template>
  <div id="app">
    <main>
      <div class="container my-5">
        <h1 class="title text-centre">Weather</h1>
      </div>
      <div class="search-box">
        <InfoMeteorologica class="list" v-bind:llistat-ciutats="ciutats"  @click='itemClicked(ciutat)'></InfoMeteorologica>
      </div>
    </main>
  </div>
</template>

<script>
import InfoMeteorologica from "@/components/InfoMeteorologica";

export default {
  name: 'App',
  data: function (){
    return{
      ciutats: [
        "Barcelona",
        "Lleida",
        "Zaragoza",
        "Sevilla",
        "Madrid",
        "Paris",
        "Melbourne",
        "Moscow",
        "Pekin",
        "Marrakech"]
    }
  },
  components: {
    InfoMeteorologica
  }



}
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body{
  font-family: 'montserrat', SansSerif;
}

#app{
  background-image: url("./assets/bckground.jpg");
  background-size: cover;
  background-position: bottom;
}

main{
  min-height: 100vh;
  padding: 25px;
  background-image: linear-gradient(to bottom, rgba(0,0,0,0.25), rgba(0,0,0,0.75));
}

.container{
  display: block;
  width: 100%;
  padding: 15px;
  color: #313131;
  font-size: 30px;
  font-weight: 900;
  text-shadow: 1px 3px rgba(0, 0, 0, 0.25);

}

.list{
  display: block;
  width: 100%;
  padding: 15px;

  color: #313131;
  font-size: 20px;

  appearance: none;
  border: none;
  outline: none;
  background: none;

  background-color: rgba(255,255,255, 0.5);
  border-radius: 0px 16px 0px 16px;
}

.location-box .location{
  color: #FFF;
  font-size: 32px;
  font-weight: 500;
  text-align: center;
  text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
}
.weather-box{
  text-align: center;
}

.weather-box .temp{
  display: inline-block;
  padding: 10px 25px;
  color: #FFF;
  font-size: 102px;
  font-weight: 900;

  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.25);
  border-radius: 16px;
  margin: 30px 0px;

  box-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}

.weather-box .weather{
  color: #FFF;
  font-size: 48px;
  font-weight: 700;
  font-style: italic;
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}

</style>
