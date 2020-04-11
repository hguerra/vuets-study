<template>
  <div id="app">
    <h1>Blog</h1>
    <BlogPost v-for="blogPost in blogPosts" :post="blogPost" :key="blogPost.title" />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import BlogPost, { Post } from './components/BlogPost.vue';

@Component({
  components: {
    BlogPost
  }
})
export default class App extends Vue {
  private blogPosts: Post[] = [
    {
      title: "Primeiro",
      body: "Lorem ipsum dolor sit amet.",
      author: "Heitor",
      datePosted: new Date(2019, 1, 18)
    },
    {
      title: "Segundo",
      body: "Lorem ipsum dolor sit amet.",
      author: "Heitor",
      datePosted: new Date(2019, 1, 19)
    },
    {
      title: "Terceiro",
      body: "Lorem ipsum dolor sit amet.",
      author: "Heitor",
      datePosted: new Date(2019, 1, 20)
    }
  ];
}
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
