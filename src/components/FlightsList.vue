<template lang="html">
  <div id="flightslist">
    <h3>Flights</h3>
    <ul>
      <flight-list-item v-for="(flight, index) in flights" :flight="flight" :key="index"></flight-list-item>
    </ul>

  </div>

</template>


<script>
import FlightListItem from "./FlightListItem.vue"

export default {
  name: "flights-list",
  props: ['flights'],
  components: {
    "flight-list-item": FlightListItem
  }
}

</script>


<style>

</style>