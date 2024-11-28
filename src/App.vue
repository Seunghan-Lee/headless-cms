<template>
  <div id="app">
    <PostList />
  </div>
</template>

<script>
import PostList from "./components/PostList.vue";

export default {
  name: "App",
  components: {
    PostList,
  },
};
</script>

<style>
/* 기본 스타일 */
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 20px;
}
</style>