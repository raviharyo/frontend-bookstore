

<template>
<button class="btn btn-primary ms-2 mt-2" @click="num = 0">Book</button>
<button class="btn btn-warning ms-2 mt-2" @click="num = 1">Genre</button>
<!-- <pre>{{Books}}</pre> -->
<div v-if="num == 0">
<ListBook :dataBook = "Books" />
</div>
<div v-else>
<ListGenre :dataGenre = "Genre" />
</div>
</template>

<script>
import axios from 'axios'
import ListBook from "./components/ListBook.vue";
import ListGenre from "./components/ListGenre.vue";
export default {
  components: { ListBook,ListGenre },
  data() {
    return {
      Books: [],
      Genre: [],
      num: 0
    };
  },
  mounted() {
    axios
    .get(`http://localhost:3000/book`)
    .then(data => this.Books = data.data)
    .catch(err => console.log(err));
    axios
    .get(`http://localhost:3000/genre`)
     .then(datag => this.Genre = datag.data)
    .catch(err => console.log(err));
  },
};
</script>
<style></style>
