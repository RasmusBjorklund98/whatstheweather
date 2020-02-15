<template>
  <div id="search">
    <div class="search-box">
      <input
        type="text"
        class="search-bar"
        placeholder="Search..."
        v-model="query"
        v-on:keypress="fetchWeather"
      />
    </div>

    <div class="weather-wrap" v-if="typeof weather.main != 'undefined'">
      <div class="location-box">
        <div class="location">{{weather.name}}, {{weather.sys.country}}</div>
        <div class="date">{{dateBuilder()}}</div>
      </div>

      <div class="weather-box">
        <div class="temp">{{Math.round(weather.main.temp)}} c</div>
        <div class="weather">{{weather.weather[0].main}}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'search', 
  data() {
    return {
      api_key: "a2bc3193968efa0fc1f7ae5b61e060fc",
      url_base: "https://api.openweathermap.org/data/2.5/",
      query: "",
      weather: {}
    };
  },
  methods: {
    fetchWeather(e) {
      if (e.key == "Enter") {
        fetch(
          `${this.url_base}weather?q=${this.query}&units=metric&APPID=${this.api_key}`
        )
          .then(res => {
            return res.json();
          })
          .then(this.setResults);
      }
    },
    setResults(results) {
      this.weather = results;
    },
    dateBuilder() {
      let d = new Date();
      let months = [
        "January",
        "February",
        "March",
        "April",
        "May",
        "June",
        "July",
        "August",
        "September",
        "October",
        "November",
        "December"
      ];
      let days = [
        "Sunday",
        "Monday",
        "Tuesday",
        "Wednesday",
        "Thursday",
        "Friday",
        "Saturday"
      ];
      let day = days[d.getDay()];
      let date = d.getDate();
      let month = months[d.getMonth()];
      let year = d.getFullYear();
      return `${day} ${date} ${month} ${year}`;
    }
  }
};
</script>

<style>

.search-box {
  width: 100%;
  margin-bottom: 2rem;
}

.search-box .search-bar {
  display: block;
  width: 100%;
  padding: 1rem;

  color: #313131;
  font-size: 2rem;

  appearance: none;
  border: none;
  outline: none;
  background: none;

  background-color: rgba(255, 255, 255, 0.7);
  border-radius: 0 1rem 0 1rem;
  transition: 0.4s;
}

.search-box .search-bar:focus {
  box-shadow: 0 0 1rem rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.5);
  border-radius: 1rem 0 1rem 0;
}

.location-box .location {
  color: #fff;
  font-size: 2rem;
  font-weight: 500;
  text-align: center;
  text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
}

.location-box .date {
  color: #fff;
  font-size: 1.5rem;
  font-weight: 300;
  font-style: italic;
  text-align: center;
  text-shadow: 1px 3px rgba(0, 0, 0, 0.25);
}

.weather-box {
  text-align: center;
}

.weather-box .temp {
  display: inline-block;
  padding: 0.75rem 1.5rem;
  color: #fff;
  font-size: 9rem;
  font-weight: 900;

  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.25);
  border-radius: 1rem;
  margin: 2rem 0;

  box-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}

.weather-box .weather {
  color: #fff;
  font-size: 3rem;
  font-weight: 700;
  font-style: italic;
  text-shadow: 3px 6px rgba(0, 0, 0, 0.25);
}
</style>
