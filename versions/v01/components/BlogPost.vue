<template>
  <div class="blogpost">
    <h2>{{ post.title }}</h2>
    <p>{{ post.body }}</p>
    <p class="meta">Written by {{ post.author }} on {{ date }}</p>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

export interface Post {
  title: string;
  body: string;
  author: string;
  datePosted: Date;
}

@Component
export default class BlogPost extends Vue {
  @Prop({type: Object as () => Post}) private post!: Post;

  get date() {
    return `${this.post.datePosted.getDate()}/${this.post.datePosted.getMonth()}/${this.post.datePosted.getFullYear()}`;
  }
}
</script>

<style lang="scss">
div.blogpost {
  h2 {
    text-decoration: underline;
  }
  p.meta {
    font-style: italic;
  }
}
</style>
