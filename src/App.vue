<template lang = "html">
  <div id="app">
  <main>
    <div>
     <h1>Edinburgh Airport  - Flight Information</h1>
     <table>
         <thead>
        <tr>
         <th class="flightRow hidden-sm hidden-xs">Airline</th>
         <th>Time</th>
         <th>Flight</th>
         <th>From/ To</th>
         <th>Status</th>
        </tr>
        </thead>
     <flights-list v-for="flight in flights" :flight="flight"></flights-list>
      </table>
    </div>
  </main>
  </div>
</template>


<script>
import FlightsList from "./components/FlightsList.vue"

export default {
  name: "app",
  data() {
    return {
      flights: []
    };
  },
  components: {
    "flights-list": FlightsList
  },
  mounted() {
    fetch('https://kabrudle.edinburghairport.com/api/flights/all')
    .then(res => res.json())
    .then(flights => this.flights = flights)
  }
}
</script>


<style>
main{
  background-image: URL("https://s3-eu-west-1.amazonaws.com/edinburghairport/files/img/clouds.jpg") !important;
  background-repeat: repeat-x;
  padding-top: 100px;
  font-family: Calibri, Arial;
  font-size: 15px;
}

th {
  color: white;
  text-transform: uppercase;
  padding: 10px;
  text-align: left;
  font-size: 20px;
}
</style>