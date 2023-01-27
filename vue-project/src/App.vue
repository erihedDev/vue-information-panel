<script>
  import Weather from './components/Weather.vue';

  var currentDate = new Date();

  var weekday=new Array(7);
  weekday[0]="Monday";
  weekday[1]="Tuesday";
  weekday[2]="Wednesday";
  weekday[3]="Thursday";
  weekday[4]="Friday";
  weekday[5]="Saturday";
  weekday[6]="Sunday";


  
  export default {
    data() {
      return {
        now: new Date().toLocaleTimeString(),
        day: weekday[currentDate.getDay() - 1],

      };
    },

    components: { Weather },

    mounted() {

      setInterval(() => {
        this.now = new Date().toLocaleTimeString();
      }, 1000);
    }
  };
</script>

<template>
  <header class="container">
    <h1>Hello, Erik Hedlund</h1>
  </header>
  <main>
    <div class="container">
      <h2>Today is {{ day }}</h2>
    </div>
    <div class="container">
      <h2>{{ now }}</h2>
    </div>
    <div class="container">
      <h2>Weather</h2>
      <Weather/>
    </div>
    <div class="container">
      <h2>News</h2>
    </div>
  </main>
</template>