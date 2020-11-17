<template>
 <div>
  <div id="app">
    <app-header/>
    <div class="container">
      <router-view/>
    </div>
    
  </div>
  </div>
</template>


<script>
import Header from './components/Header.vue'
export default {
    components:{
      'app-header':Header
    }
}
</script>

<style scoped>
body {
  background: #222831;
}
.container {
  max-width: 900px;
}
.card {
  background: #1a1d24;
}
.card-body {
  color: #f9ffee;
}
.card-body a {
  color: #efbb35;
}
</style>
