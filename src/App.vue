<template lang = "html">
    <main>
      <div class="container">
      <div class="column">
      <h1>Flight Arrivals</h1>
      <!-- <img class="imgarr" alt="Arrivals" src="https://s3-eu-west-1.amazonaws.com/edinburghairport/files/img/flights/w_arrivals.png"> -->
        <table>
          <tbody>
          <thead>
            <tr>
              <th>Airline</th>
              <th>Time</th>
              <th>Flight</th>
              <th>From</th>
              <th>Status</th>
              <th>Info</th>
            </tr>
          </thead>
          <flights-list v-for="(flight, index) in flights" :flight="flight" :key="index" v-if="flight.ArrDep === 'A'"></flights-list>
          </tbody>
        </table>
      </div>
      <div class="column">
      <h1>Flight Departures</h1>
      <!-- <img class="imgdep" alt="Departures" src="https://s3-eu-west-1.amazonaws.com/edinburghairport/files/img/flights/w_departures.png"> -->
        <table>
          <tbody>
          <thead>
            <tr>
              <th>Airline</th>
              <th>Time</th>
              <th>Flight</th>
              <th>To</th>
              <th>Status</th>
              <th>Info</th>
            </tr>
          </thead>
          <flights-list v-for="(flight, index) in flights" :flight="flight" :key="index" v-if="flight.ArrDep === 'D'"></flights-list>
          </tbody>
        </table>
      </div>
      </div>
    </main>
</template>

<script>
import FlightsList from "./components/FlightsList.vue";

export default {
  name: "app",
  data() {
    return {
      flights: [],
      timer: ""
    };
  },
  components: {
    "flights-list": FlightsList
  },
  mounted() {
    this.fetchFlights();
  },
  created() {
    this.fetchFlights();
    this.timer = setInterval(this.fetchFlights, 30000);
  },
  methods: {
    fetchFlights() {
      fetch("https://kabrudle.edinburghairport.com/api/flights/all")
        .then(res => res.json())
        .then(flights => (this.flights = flights));
    }
  }
};
</script>

<style>
/* @media only screen and (max-width: 768px), (min-device-width: 768px) and (max-device-width: 1024px){
  table{
    font-size: 12px;
  }
} */

main {
  background-image: URL("https://s3-eu-west-1.amazonaws.com/edinburghairport/files/img/clouds.jpg");
  background-repeat: no-repeat;
  background-size: contain;
  padding-top: 30px;
  font-family: Calibri, Arial;
  font-size: 15px;
}

.container {
    content: "";
    display: table;
    padding-left: 30px;
}
@media (min-width: 768px){
.column {
  float: left;
  width: 50%;
  position: relative;
  min-height: 1px;
  /* padding-left: 15px;
  padding-right:15px; */
}}

table {
  background-color: black;
  border-collapse: collapse;
  line-height: 1.42857;
}

h1 {
  padding-left: 200px;
}

th {
  color: white;
  text-transform: uppercase;
  padding: 10px;
  text-align: left;
  font-size: 20px;
}

td {
  text-transform: uppercase;
  color: white;
  padding: 10px;
}

</style>