<template>
  <div class="home">
    <div v-if="error">{{ error }}</div>
    <div v-for="post in posts" :key="post.id">
      <h2>{{ post.title }}</h2>
      <p>{{ post.author }}</p>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from "axios";

export default {
  name: "Home",
  components: {},
  data() {
    return {
      posts: null,
      error: null,
    };
  },
  created() {
    axios
      .get("http://localhost:3000/posts")
      .then((response) => {
        this.posts = response.data;
        console.log(repsonse.data);
      })
      .catch((e) => {
        this.error = e.message;
      });
  },
};
</script>
