<template>
  <h1>Post</h1>
  <form v-on:submit.prevent>
    <label class="label">Title</label>
    <input type="text" v-model="postBody.title" />
    <label class="label">Body</label>
    <input type="text" v-model="postBody.body" />
    <button type="submit" v-on:click="addNewPost">add new Post</button>
  </form>
</template>

<script>
import axios from "axios";

export default {
  name: "Post",
  data() {
    return {
      postBody: {
        title: "",
        body: "",
      },
    };
  },
  methods: {
    addNewPost() {
      axios
        .post("https://jsonplaceholder.typicode.com/posts", this.postBody)
        .then((response) => {
          console.log("response", response);
        })
        .catch((e) => {
          this.errors.push(e);
        });
    },
  },
};
</script>
