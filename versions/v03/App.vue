<template>
  <div id="app">
    <h1>Blog</h1>
    <button @click="toggleHighlightedPostsVisibility">{{ showHighlighted ? 'Hide' : 'Show' }} highlighted posts</button>
    <BlogPost v-for="blogPost in visibleBlogPosts" :post="blogPost" :key="blogPost.title" />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import BlogPost, { Post } from "./components/BlogPost.vue";

@Component({
  components: {
    BlogPost
  }
})
export default class App extends Vue {
  public showHighlighted = true;

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
      datePosted: new Date(2019, 1, 19),
      highlighted: true
    },
    {
      title: "Terceiro",
      body: "Lorem ipsum dolor sit amet.",
      author: "Heitor",
      datePosted: new Date(2019, 1, 20)
    }
  ];

  get visibleBlogPosts() {
    return this.blogPosts.filter(
      (post: Post) =>
        post.highlighted === undefined ||
        post.highlighted === this.showHighlighted
    );
  }

  public toggleHighlightedPostsVisibility() {
    this.showHighlighted = !this.showHighlighted;
  }
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
