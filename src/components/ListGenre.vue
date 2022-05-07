<template>
<div class="container"> 
    <h3 class="text-center">Table Genre</h3>
    <table class="table">
  <thead>
    <tr>
      <th scope="col">No</th>
      <th scope="col">Genre</th>
     
    </tr>
  </thead>
  <tbody>
    <tr v-for="list in dataGenre.data" :key="list.data">
      <th>{{list.id}}</th>
      <td>{{list.name}}</td>
   
    </tr>
  </tbody>
</table>
</div>
</template>

<script>
export default {
name: `ListGenre`,
props: ['dataGenre']
}
</script>

<style>

</style>