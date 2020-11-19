<template>
    <div class="post-detail">
      
  <div class="row mb-3">
      <div class="col-auto">
        <router-link class="btn btn-block btn-info" to="/">Go Back</router-link>
      </div>
    </div>
    <div class="card mb-3 bg-light">
      <div class="card-body">
        <h3> {{post.title}}</h3>
        <p class="text-info">{{post.body}}</p>
      </div>
    </div>
 <app-postcomments/>
    </div>
</template>



<script>

import axios from 'axios'
import postcomments from '../components/PostComments'

export default {
  name:'PostDetail',
  components:{
    'app-postcomments' : postcomments
  },
  data(){
    return{
      id: this.$route.params.id,
      post:[],
    }
  },
  created() {
    axios
      .get(`https://jsonplaceholder.typicode.com/posts/${this.id}`)
      .then((resp) => {
        console.log(resp.data)
        this.post = resp.data;
      })
      .catch((e) => {
        console.log(e.message)
      });
  },
}
</script>

<style scoped>
  .btn-info{
    margin-top:10px
  }
</style>