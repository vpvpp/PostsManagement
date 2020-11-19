<template>
  <div class="home">
    <div>
      <app-addpost @newPost="RecievedNewPost" />
    </div>
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
  methods: {
    RecievedNewPost(newpostData) {
      const { title, body } = newpostData;

      axios
        .post("https://jsonplaceholder.typicode.com/posts", {
          //  es6 destrucring
              title : title,
              body: body
        })
        .then( response => {
          // //spread Operator
            this.postslist = [...this.postslist, response.data]
        })
        .catch( error =>  {
          console.log(error);
        });
    },
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
