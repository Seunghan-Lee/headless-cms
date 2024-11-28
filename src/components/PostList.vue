<template>
  <div>
    <h1>WordPress Posts</h1>
    <ul>
      <li v-for="post in posts" :key="post.id">
        <a :href="post.link" target="_blank">
          <h2 v-html="post.title.rendered"></h2>
        </a>
        <p><strong>Posted on:</strong> {{ new Date(post.date).toLocaleDateString() }}</p>
        <p v-html="post.excerpt.rendered"></p>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "PostList",
  data() {
    return {
      posts: [],
    };
  },
  mounted() {
    axios
      .get("http://localhost:10008/wp-json/wp/v2/posts") // 워드프레스 REST API URL
      .then((response) => {
        this.posts = response.data;
      })
      .catch((error) => {
        console.error("Error fetching posts:", error);
        alert("Failed to load posts. Please check your WordPress API.");
      });
  },
};
</script>

<style>
/* 간단한 스타일 */
ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin-bottom: 20px;
  border-bottom: 1px solid #ddd;
  padding-bottom: 10px;
}

a {
  text-decoration: none;
  color: #333;
}
</style>