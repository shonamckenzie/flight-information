<template lang = "html">
  <div id="app">
    <main>
      <div class="container">
      <div class="column">
      <h1>Edinburgh Airport  - Flight Arrivals</h1>
        <table>
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
        </table>
      </div>
      <div class="column">
      <h1>Edinburgh Airport  - Flight Departures</h1>
        <table>
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
        </table>
      </div>
      </div>
    </main>
  </div>
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
main {
  background-image: URL("https://s3-eu-west-1.amazonaws.com/edinburghairport/files/img/clouds.jpg") !important;
  background-repeat: repeat-x;
  padding-top: 30px;
  font-family: Calibri, Arial;
  font-size: 15px;
}

.column {
    float: left;
    width: 50%;
}

/* Clear floats after the columns */
.container:after {
    content: "";
    display: table;
    clear: both;
}

table {
  /* width: 100px; */
  /* content: " ";
  display: table; */
  background-color: black;
  border-collapse: collapse;
  /* margin: 0 auto; */
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