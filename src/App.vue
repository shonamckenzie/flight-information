<template lang = "html">
  <div>
    <h1>Edinburgh Airport  - Flight Information</h1>
    <flights-list :flights="flights"></flights-list>
  </div>

</template>


<script>
import FlightsList from "./components/FlightsList.vue"

export default {
  name: "app",
  data() {
    return {
      flights: [],
      selectedFlight: null
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
</style>