<template>
  <div class="home">
    <h1>Hi vinod...this is home component</h1>
    <app-addpost />
    <app-postlist :postslists="postslist" :errors="errors" />
  </div>
</template>

<script>
// @ is an alias to /src

import axios from "axios";
import postlist from "../components/PostList.vue";
import addpost from "../components/AddPost.vue";

export default {
  name: "Home", 
  components: {
    "app-postlist": postlist,
    "app-addpost": addpost,
  },
  data() {
    return {
      postslist: [],
      errors: [],
    };
  },
  created() {
    axios
      .get(`https://jsonplaceholder.typicode.com/posts?_limit=5`)
      .then((resp) => {
        //console.log(resp.data)
        this.postslist = resp.data;
      })
      .catch((e) => {
        this.errors.push(e);
      });
  },
};
</script>
