<template>
<div class="add-post"> 
   
   <div class="row mb-3">
      <div class="col text-right">
        <button class="btn btn-primary" v-on:click="showform">Create New Post</button>
      </div>
    </div>
    <div class="card mb-3" v-if="formDiv">
      <div class="card-body">
        <form @submit.prevent="addPost">
          <div class="form-group">
            <label>Post Title</label>
            <input
              v-model="title"
              type="text"
              name="title"
              class="form-control"
              placeholder="Enter post title"
            >
          </div>
          <div class="form-group">
            <label>Post Details</label>
            <textarea
              v-model="body"
              name="body"
              class="form-control"
              placeholder="Enter post details"
            ></textarea>
          </div>
          <div class="row">
            <div class="col-6 mx-auto">
              <button class="btn btn-block btn-success">Create Post</button>
            </div>
          </div>
        </form>
      </div>
    </div>
    </div>
</template>

<script>
export default {
   name:'AddPost',
   data(){
      return{
           formDiv:false,
           title:"",
           body:""

      }
   },
   methods:{
      showform(){
          this.formDiv = true;
      },

      addPost(){

         const newdata = {
             title :this.title,
             body :this.body
         }

         this.$emit('newPost',newdata);
         this.title = "";
         this.body="";
      }
   }
}
</script>

<style scoped>
  .btn .btn-primary{
     margin-top: 10px;
     align-self: left;
  }
</style>