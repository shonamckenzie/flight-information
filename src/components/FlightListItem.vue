<template lang="html">
  <li>{{flight.Airline}} {{flight.Time}} {{ flight.FlightNo}} {{flight.PortOfCallA}}  {{flight.Status}}</li>
</template>


<script>

export default {
  name: "flight-list-item",
  props: ['flight']
}
</script>


<style>
li {
  list-style-type: none;
}
</style>