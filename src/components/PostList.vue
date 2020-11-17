<template>
  <div class="post-list">
    <div class="card mb-3" v-for="post in postslists" :key="post.id">
      <div class="card-header">
        <h4>Post ID : {{ post.id }}</h4>
      </div>
      <div class="card-body">
        <h5 class="card-title">{{ post.title }}</h5>
        <!-- <a href="#" class="btn btn-primary">show comments</a> -->    
      <router-link tag="button" 
      :to="`/PostDetail/${post.id}`"
       class="btn btn-primary">show post details</router-link> 

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


export default {
  name: "PostList",
  props: ["postslists", "errors"],
};
</script>

<style scoped >


</style>