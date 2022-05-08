<template>
<div>
</div>
<div>
</div>
  <form @submit.prevent="postData" method="post">
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
            page:0
        },
        backToList: false
    }
},
 methods: {
     postData(){
        // console.log(this.form);
        let data = JSON.stringify(this.form)
       console.log(this.form);
      console.log(data);
         axios.post('http://localhost:3000/book',{title: this.form.title, author: this.form.author, page:this.form.page})
         .then((res)=>{
            //  console.log(res)
             this.form.title = ''
             this.form.author = ''
             this.form.page = 0
         })
         .catch((err)=>{
             console.log(err.message,'ee')
         });

     }
 }
}

</script>

<style>

</style>