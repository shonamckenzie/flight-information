<template lang="html">
        <tbody>
        <tr class="flightRow hidden-sm hidden-xs">
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


<style>
table {
  content: " ";
  display: table;
  background-color: black;
}
td {
  text-transform: uppercase;
  color: white;
  padding: 10px;
}


tbody {
  color: white;
}



</style>