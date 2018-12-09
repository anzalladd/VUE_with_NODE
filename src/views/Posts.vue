<template>
  <div class="about">
    <h1>This is an Post page</h1>
    <div v-for="post in posts">
      <span><b>{{post.title}}</b></span>
      <br>
      <span>{{post.description}}</span>
    </div>
  </div>
</template>

<script>
import PostsService from '@/services/PostsService'
  export default{
    name: 'posts',
    data(){
      return{
        posts:[]
      }
    },
     mounted() {
    this.getPosts();
  },
  methods: {
    async getPosts () {
      const response = await PostsService.fetchPosts()
      this.posts = response.data
    }
  }
  }
 

</script>

<style lang="scss" scoped>
 .about > div{
   margin-top: 50px;
 }
</style>
