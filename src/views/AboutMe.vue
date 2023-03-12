<template>
    <div class="container">
        <h1>this is an about page</h1>        
          <div v-for="post in posts" v-bind:key="post.id">
            <div class="border border-primary mt-1">
                <h5> {{ post.title }}</h5>
                <p> {{ post.body }}</p>
            </div>
          </div>
    </div>
</template>

<script>
const URI = "https://jsonplaceholder.typicode.com/posts";
export default {
    data(){
     return {
        posts: []
     }
    },
    created() {
      this.getPost();
    },
    methods: {
        async getPost(){
          const response = await fetch(URI);
          const data = await response.json();
          this.posts = data;
        }
    }

}
 
</script>

<style scoped>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>