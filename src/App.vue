<template lang = "html">
  <div>
    <h1>Edinburgh Airport  - Flight Information</h1>
  </div>

</template>


<script>

export default {
  name: "app",
  data() {
    return {
      flights: [],
      selectedFlight: null
    };
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