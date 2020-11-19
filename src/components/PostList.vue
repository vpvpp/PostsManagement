<template>
  <div class="post-list">
    <div class="card mb-3" v-for="post in postslists"  :key="post.id"  >
      <div class="card-header">
        <!-- <h4>Post ID : {{ post.id }}</h4> -->
      </div>
      <div class="card-body">
      <h5 class="card-title">{{ post.title }}</h5>
      <p class="text-info">{{post.body}}</p>
        <!-- <a href="#" class="btn btn-primary">show comments</a> -->    
      <router-link tag="button" 
      :to="`/PostDetail/${post.id}`"
       class="btn btn-primary">postdetails</router-link>

        <button   class="btn btn-danger"  @click="deletepost(post.id)"> Delete Post </button>
      </div>
    </div>

    <div class="card mb-3" v-if="errors && errors.length">
      <div class="card-body">
        <p v-for="(error, index) of errors" :key="index">{{ error.message }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import Axios from 'axios'


export default {
  name: "PostList",
  props: ["postslists", "errors"],
  methods:{
    deletepost(id){
    Axios.delete(`https://jsonplaceholder.typicode.com/posts/${id}`)
    .then( response => {
      this.postslists.splice(response.data.id, 1);
      console.log(this.postslists);
    }).catch(err => {
      console.log(err.message);
    })
   
   }
  }
}
</script>

<style scoped >
 .btn-danger {
     margin-left: 15px;
 }

</style>