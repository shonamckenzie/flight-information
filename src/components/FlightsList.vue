<template lang="html">
  <tbody>
    <tr>
     <td>{{flight.Airline}}</td>
     <td>{{flight.Time}}</td>
     <td>{{flight.FlightNo}}</td>
     <td>{{flight.PortOfCallA}}</td>
     <td>{{flight.Status}}</td> 
     <td>{{flight.ArrDep}}</td>
    </tr>
  </tbody> 
</template>

<script>
export default {
  name: "flights-list",
  props: ['flight']
}
</script>

<style lang="css" scoped>



</style>