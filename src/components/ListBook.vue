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
       <th scope="col">Action</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="(list, index) in dataBook.data" :key="list.data">
      <th>{{index+1}}</th>
      <td>{{list.title}}</td>
      <td>{{list.author}}</td>
      <td>{{list.page}}</td>
       <td><button class="btn btn-warning">Edit</button> <button @click.prevent="deleteBooks(list.id)" class="btn btn-danger">Delete</button> </td>
    </tr>
  </tbody>
</table>
</div>
    </div>
</template>
<script>
import formAddBook from './formAddBook.vue'
import axios from 'axios'
export default {
    components: {formAddBook},
    name: `ListBook`,
    props: ['dataBook'],
    data(){
        return {
            openForm : false
        }
    },
    methods:{
      updateBooks(id){
        axios.get(`http://localhost:3000/book/${id}`)
        
      },
      deleteBooks(id){
        axios.delete(`http://localhost:3000/book/${id}`)
        .then(res=>{
          console.log(`success delete data`);
        })
        .catch(err=>{
          console.log(err.message);
        })
      }
    }    
}
</script>