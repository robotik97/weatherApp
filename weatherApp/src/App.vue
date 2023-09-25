<script>
import axios from 'axios'
export default {
  data() {
    return {
      city: "",
      error: "",
      info: null
    }
  },
  computed: {
    cityName() {
      return "«" + this.city + "»"
    },
    showTemp() {
      return "Temperature:" + this.info.main.temp
    },
    showFellsLike() {
      return "Feels like:" + this.info.main.feels_like
    },
    showMinTemp() {
      return "Min temperature:" + this.info.main.temp_min
    },
    showMaxTemp() {
      return "Max temperature:" + this.info.main.temp_max
    }
  },
  methods: {
    getWeather() {
      if (this.city.trim().length < 2) {
        this.error = "enter more than two characters"
        return false
      }
      this.error = ""
      axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&appid=32e8dbc84883eeb465b483cef6342220`)
        .then(result => (this.info = result.data))
    }
  }

}
</script>

<template>
  <div class="wrapper">
    <h1>weather app</h1>         
    <p>find out the weather in {{ city == "" ? "your city" : cityName }}</p>
    <input type="text" v-model="city" placeholder="enter city">
    <!-- changing button -->
    <!-- if the input is empty, then the button does not work -->
    <button v-if="city !== ''" @click="getWeather()">push here</button>
    <button disabled v-else="city==''">enter the name of the city</button>
    <p class="error">{{ error }}</p>
    <div v-if="info != null">
      <p>{{ showTemp }}</p>
      <p>{{ showFellsLike }}</p>
      <p>{{ showMinTemp }}</p>
      <p>{{ showMaxTemp }}</p>
    </div>
  </div>
</template>

<style scoped>
.error {
  color: rgb(236, 39, 49);
}

.wrapper {
  width: 400px;
  height: 250px;
  border-radius: 50px;
  /* color: #4c4e4a; */
  padding: 20px;
  background: #74e70e;
  text-align: center;
  margin-top: 50px;
}

.wrapper button {
  margin: 10px;
  background: rgb(38, 38, 39);
  border-radius: 25px;
  padding: 5px 10px;
  outline: none;
  color: #797b74;
}

.wrapper input {
  background: #74e70e;
  border: none;
  border-radius: 25px;
  padding: 5px 10px;
  font-size: 14px;
}

.wrapper button:disabled {
  background: rgb(73, 73, 74);
}

.wrapper input:focus {
  border-bottom-color: rgb(38, 38, 39);
  border: none;
}

.wrapper button:hover {
  transform: scale(1.1) translateY(-5px);
  color: rgb(234, 255, 100);
}
</style>
