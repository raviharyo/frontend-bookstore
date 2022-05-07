<template>
<div>
</div>
<div>
</div>
  <form @submit="postData(e)" method="post">
  <div class="mb-3">
    <label for="exampleInputEmail1" class="form-label">Title</label>
    <input type="text" v-model="form.title" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp">
  
  </div>
  <div class="mb-3">
    <label for="exampleInputPassword1" class="form-label">Author</label>
    <input type="text" v-model="form.author" class="form-control" id="exampleInputPassword1">
  </div>
  <div class="mb-3">
    <label for="exampleInputPassword1" class="form-label">Page</label>
    <input type="number" v-model="form.page" class="form-control" id="exampleInputPassword1">
  </div>
  
  <button type="submit" class="btn btn-primary">Submit</button>
</form>
<button type="submit" class="btn btn-danger mt-2" @click="backToList = true">Cancel</button>
</template>
<script>
import axios from 'axios'
export default {
name: `formAddBook`,
data(){
    return{
        form:{
            title: '',
            author: '',
            page:''
        },
        backToList: false
    }
},
 methods: {
     postData(e){
        // console.log(this.form);
        e.preventDefault()
         axios.post('http://localhost:3000/book', this.form)
         .then((res)=>{
           
             console.log(res);
         })
         .catch((err)=>{
             console.log(err);
         })

     }
 }
}

</script>

<style>

</style>