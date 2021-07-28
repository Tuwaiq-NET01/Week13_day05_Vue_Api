<template>
  <h1>Home</h1>
  <ul>
    <li v-for="post in posts" v-bind:key="post.id">
      <h3>{{ post.title }}</h3>
    </li>
  </ul>
</template>

<script>
import axios from "axios";

export default {
  name: "Home",
  data() {
    return {
      posts: [],
    };
  },
  components: {},
  created() {
    axios.get("https://jsonplaceholder.typicode.com/posts").then((response) => {
      // JSON responses are automatically parsed.
      console.log("response", response);
      this.posts = response.data;
    });
  },
};
</script>

<style>
</style>
