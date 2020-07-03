<template>
  <div id="app" :class="typeof weather.main != 'undefined' && weather.main.temp > 78 ? 'warm' : ''">
    <main>
        <div class="search-box">
            <input 
                type="text" 
                class="search-bar" 
                placeholder="Search..." 
                v-model="query" 
                @keyup.enter="fetchWeather" />
        </div>
        <div class="weather-wrap" v-if="typeof weather.main != 'undefined'">
            <div class="location-box">
                <div class="location">{{weather.name}}, {{weather.sys.country}}</div>
                <div class="date">{{ dateBuilder() }}</div>
            </div>
            <div class="weather-box">
                <div class="temp">{{ Math.round(weather.main.temp) }}deg f</div>
                <div class="weather">{{weather.weather[0].main}}</div>
            </div>
        </div>
    </main>
  </div>
</template>

<script>
export default {
  name: 'App',
  data () {
      return {
          api_key: '51ea9ae87e1e6e61855dd280d136f933',
          url_base: "https://api.openweathermap.org/data/2.5/",
          query: '',
          weather: {}
      }
  },
  methods: {
      fetchWeather () {
          fetch(`${this.url_base}weather?q=${this.query}&units=imperial&APPID=${this.api_key}`)
          .then(res => {
              return res.json();
          }).then(this.setResults);
      },
      setResults (results) {
          this.weather = results;
      },
      dateBuilder () {
          let d = new Date();
          let months = ["January","February","March","April","May","June","July","August","September","October","November","December"];
          let days = ["Sunday","Monday","Tuesday","Wednesday","Thursday","Friday","Saturday"];

          let day = days[d.getDay()];
          let date = d.getDate();
          let month = months[d.getMonth()];
          let year = d.getFullYear();

          return `${day} ${date} ${month} ${year}`;
      }
  }
}
</script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

#app {
    background-image: url('./assets/cold-bg.jpg');
    background-size: cover;
    background-position: bottom;
    transition: all 0.4s ease-in-out;
}

#app.warm {
    background-image: url('./assets/warm-bg.jpg');
}

main {
    min-height: 100vh;
    padding: 25px;
    background-image: linear-gradient(to bottom, rgba(0,0,0,0.25), rgba(0,0,0,0.75));
}

.search-box {
    width: 100%;
    margin-bottom: 30px;
}

.search-bar {
    display: block;
    width: 100%;
    padding: 15px;
    color: #313131;
    font-size: 20px;
    appearance: none;
    border: none;
    outline: none;
    background-color: rgba(255,255,255,0.5);
    border-radius: 0 15px 0 15px;
    transition: 0.4s ease-in-out;
}

.search-bar:focus {
    background-color: rgba(0,0,0,0.75);
    box-shadow: 0 0 16 rgba(0,0,0,0.25);
    border-radius: 16px 0 10px 0;
}

.location {
    color: #fff;
    font-size: 32px;
    font-weight: 500;
    text-align: center;
    text-shadow: 1px 3px rgba (0,0,0,0.25);
}

.date {
    color: #fff;
    font-size: 20px;
    font-weight: 300;
    text-align: center;
    font-style: italic;
}

.weather-box {
    text-align: center;
}

.temp {
    color: #fff;
    display: inline-block;
    padding: 10px 25px;
    font-size: 102px;
    font-weight: 900;
    text-shadow: 3px 6px rgba(0,0,0,0.25);
    background-color: rgba(255,255,255,0.25);
    border-radius: 15px;
    margin: 30px 0;
    box-shadow: 3px 6px rgba(0,0,0,0.25);
}

.weather {
    color: #fff;
    font-size: 48px;
    font-weight: 700;
    font-style: italic;
    text-shadow: 3px 6px rgba(0,0,0,0.25);
}
</style>
