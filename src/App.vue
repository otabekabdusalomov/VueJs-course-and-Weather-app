<template>
  <div id="app">
    <main>
      <div class="search-box">
        <input class="search-bar" type="text" placeholder="search">
      </div>

      <div class="weather-wrapper">
        <div class="location-box">
          <div class="location">8'C</div>
          <div class=""></div>
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
        api_key: '66a5d7418e3b615ac32b4a539746659b'
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
</style>