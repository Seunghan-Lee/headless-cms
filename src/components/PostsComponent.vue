<template>
  <div>
    <h1>WordPress Posts</h1>
    <ul>
      <li v-for="post in posts" :key="post.id">{{ post.title.rendered }}</li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      posts: [],
    };
  },
  mounted() {
    axios
      .get("http://localhost:10001/wp-json/wp/v2/posts")
      .then((response) => {
        this.posts = response.data;
      })
      .catch((error) => {
        console.error("Error fetching posts:", error);
      });
  },
};
</script>