<template>
  <div id="app">
    <main>
      <div class="search-box">
        <input class="search-bar"
        type="text"
        placeholder="search..."
        v-model="query"
        v-on:keypress="showWeather">
      </div>
      
      <div class="weather-wrapper" v-if="typeof weather.main != 'undefined'">
        <div class="location-box">
          <div class="location">{{ weather.name }}, {{ weather.sys.country}}</div>
          <div class="weather">{{ dateBuilder() }}</div>
        </div>
        
        <div class="weather-box">
           <div class="temp">{{ Math.round(weather.main.temp) }}</div>
           <div class="weather">{{ weather.weather[0].main }}</div>
        </div>
      </div>
    </main>
  </div>
  
</template>



<script>
  export default {
    name: 'app',
    data() {
      return{
        api_key: '66a5d7418e3b615ac32b4a539746659b',
        url_base: 'https://api.openweathermap.org/data/2.5/',
        quary: '',
        weather: {},
      }
    },
    method: {
      showWeather(evt) {
        if(evt.key == 'Enter' ) {
          fetch(`${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}`)
          .then(res => {
            return res.json()
          }) .then(this.setResults)
        }
      },
      setResults(results) {
        this.weather = results
      },
      dateBuilder() {
        let d = new Date()
        let months = []
      }
    }
    
  }
</script>

<style>
  /* GENERAL CSS */
  *{
    box-sizing: border-box;
  }
  
  body{
    margin: 0;
    padding: 0;
    font-family: sans-serif;
    
  }
  .container{
    max-width: 1157px;
    margin: 0 auto;
    padding: 0 20px;
  }
  
  img {
    max-width: 100%;
    height: auto;
    display: inline-block;
  }
  
  #app{
    background-image: url('./assets/cold.jpg');
    background-size: cover;
    background-position: center;
    transition: 0.4s;
    
  }
  main{
    min-height: 100vh;
    padding: 25px;
    background-image: linear-gradient(to bottom, rgba(0,0,0,.25), rgba(0,0,0,6));
    
  }
  .search-box{
    width: 90%;
  }
  .search-box >.search-bar{
    display: block;
    width: 100%;
    padding: 15px;
    color: #3d3434;
    font-size: 20px;
    bottom: 20px;
    border: none;
    background: none;
    outline: none;
    appearance: none;
    background-color: rgba(255, 255, 255, 0.5);
    box-shadow: 0px 0px 8px rgba(0,0,0,.25);
    transition: .4s;
  }
  .search-box >.search-bar:focus{
    box-shadow: 0px 0px 16px rgba(0,0,0,.25);
    background-color: rgba(255, 255, 255, .75);
  }
  
  .location-box .location{
    margin-top: 10vh;
    color: #fff;
    font-size: 32px;
    font-weight: 500;
    text-align: center;
    text-shadow: 1px 3px rgba(0,0,0,.25);
  }
  .location-box .date{
    color: #fff;
    font-size: 20px;
    font-weight: 300;
    font-style: italic;
    text-align: center;
  }
  .location-box{
    text-align: center;
  }
  .location-box .temp{
    display: inline-block;
    padding: 10px 25px;
    color: #fff;
    font-size: 100px;
    font-weight: 900;
    text-shadow: 3px 6px rgba(0,0,0,.25);
    background-color: rgba(255, 255, 255, .25);
    border-radius: 16px;
    margin: 30px 0;
    box-shadow: 3px 6px rgba(0,0,0,.25);
  }
  .location-box .weather{
    color: #fff;
    font-size: 28px;
    font-weight: 700;
    font-style: italic;
    text-shadow: 3px 6px rgba(0,0,0,.25);
  }
</style>