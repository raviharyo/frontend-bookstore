<template>
<!-- <pre>{{dataBook.data}}</pre> -->
<div class="container">
    <button class="btn btn-primary ms-2 mt-2" @click="openForm = true">Add Book</button>
    <div v-if="openForm == true">
        <formAddBook/>
    </div>
    <div v-else>

<h3 class="text-center">Table Book</h3>
    <table class="table">
  <thead>
    <tr>
      <th scope="col">No</th>
      <th scope="col">Title</th>
      <th scope="col">Author</th>
      <th scope="col">Page</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="(list, index) in dataBook.data" :key="list.data">
      <th>{{index+1}}</th>
      <td>{{list.title}}</td>
      <td>{{list.author}}</td>
      <td>{{list.page}}</td>
    </tr>
  </tbody>
</table>
</div>
    </div>
</template>
<script>
import formAddBook from './formAddBook.vue'
export default {
    components: {formAddBook},
    name: `ListBook`,
    props: ['dataBook'],
    data(){
        return {
            openForm : false
        }
    }    
}
</script>