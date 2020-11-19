<template>
    <div class="comments">
       <div class="card  mb-3" v-for="comment in comments" :key="comment.id">
      <div class="row no-gutters bg-dark">
        <div class="col-md-2 ">
          <img src="@/assets/logo.png" class="card-img">
        </div>
        <div class="col-md-10 bg-white">
          <div class="card-body">
            <h5 class="card-title"> Comment title: {{comment.name}}</h5>
            <p class="card-text text-info"> Comment Body: {{comment.body}}</p>
            <p class="card-text">
              <small>Commentor Email: {{comment.email}}</small>
            </p>
          </div>
        </div>
      </div>
    </div>
    </div>
</template>

<script>

import axios from 'axios'

export default {
  name: "PostComments",
  data() {
    return {
      id: this.$route.params.id,
      comments: []
    };
  },
  created() {
    axios
      .get(`https://jsonplaceholder.typicode.com/comments?postId=${this.id}`)
      .then(res => {
        this.comments = res.data;
      })
      .catch(e => {
        this.errors.push(e);
      });
  }
};
</script>

<style>

</style>