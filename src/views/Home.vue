<template>
  <div>
    <div class="post" v-for="(post, i) in posts" :key="i">
      <img v-bind:src="post.picture.large" />
      <p>{{ post.name.title }} {{ post.name.first }} {{ post.name.last }}</p>
      <p>Country ` {{ post.location.country }}</p>
      <p>Email ` {{ post.email }}</p>
      <button @click="refreshPeople()">Refresh List</button>
    </div>
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

  async mounted() {
    axios
      .get("https://randomuser.me/api/?results=")
      .then((val) => (this.posts = val.data.results));
  },

  methods: {
    refreshPeople() {
      //   location.reload();
      axios
        .get("https://randomuser.me/api/?results=")
        .then((val) => (this.posts = val.data.results));
    },
  },
};
</script>

<style scoped>
.post {
  background-color: aqua;
  text-align: center;
  width: 400px;
  margin: 0 auto;
  margin-top: 5px;
}

img {
  border-radius: 50%;
}

button {
  margin: 0 auto;
  color: blue;
  border-radius: 8px;
}
</style>
