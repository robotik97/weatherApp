<script>
export default {
  data() {
    return {
      city: ""
    }
  },
  computed:{
cityName(){
return "«"+this.city+"»"
}
  }
}
</script>

<template>
  <div class="wrapper">
    <h1>weater app</h1>
    <p>find out the weather in {{ city == "" ? "your city" : cityName }}</p>
    <input type="text" v-model="city" placeholder="enter city">
    <!-- changing button -->
    <!-- if the input is empty, then the button does not work -->
    <button v-if="city !== ''">push here</button>
    <button disabled v-else="city==''">enter the name of the city</button>
  </div>
</template>

<style scoped>
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
  background:  rgb(73, 73, 74);
}

.wrapper input:focus {
  border-bottom-color: rgb(38, 38, 39);
  border: none;
}

.wrapper button:hover {
  transform: scale(1.1) translateY(-5px);
}
</style>
