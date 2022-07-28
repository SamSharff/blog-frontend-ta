<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Welcome to amanda's awesome cookbook!!",
      posts: [],
    };
  },
  created: function () {
    this.indexposts();
  },
  methods: {
    indexposts: function () {
      axios.get("/posts.json").then((response) => {
        this.posts = response.data;
        console.log("All Posts:", this.posts);
      });
    },
  },
};
</script>

<template>
  <div v-for="post in posts" v-bind:key="post.id">
    <h1>{{ post.title }}</h1>
    <img :src="post.image_url" alt="TASTY FOODS" />
    <p>
      {{ post.chef }}
    </p>
    <p>
      {{ post.prep_time }}
    </p>
  </div>
</template>
