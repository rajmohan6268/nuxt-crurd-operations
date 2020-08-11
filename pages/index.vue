<template>
  <div>
    <nuxt-link class="text-4xl font-extrabold" to="/">crud operation</nuxt-link>
    <div class="container mx-auto">
      <button class="bg-green-700 px-4 py-8" @click="savePost">post</button>
      <button class="bg-green-700 px-4 py-8" @click="getPost">get</button>
      <button class="bg-green-700 px-4 py-8" @click="updatepost">put</button>
      <button class="bg-green-700 px-4 py-8" @click="deletePost">del</button>
    </div>
    <div
      class="font-bold justify-center text-2xl"
    >crud operation in nuxt using axios in test api usning</div>
    <a
      class="text-4xl font-extrabold text-indigo-700"
      href="https://jsonplaceholder.typicode.com/guide.html"
    >
      click this link=>>>> JSONPlaceholder
      Fake Online REST API for Testing and Prototyping
    </a>
    <div
      class="font-bold justify-center text-4xl text-red-700"
    >see inspect element networks for operations</div>
    <div
      class="font-bold justify-center text-4xl text-gray-700"
    >and start clicking buttons and see the response status codes</div>

    <!-- <button class="bg-green-700 px-4 py-8" @click="savePost">post</button>
    <button class="bg-green-700 px-4 py-8" @click="getPost">get</button>
    <button class="bg-green-700 px-4 py-8" @click="updatepost">put</button>
    <button class="bg-green-700 px-4 py-8" @click="deletePost">del</button>-->
  </div>
</template>
<script>
import PostDataService from "../services/PostDataService";
export default {
  data() {
    return {
      post: {
        id: 0,
        title: "cc",
        body: "ccc",
        userId: 0,
      },
      // submitted: false,
      posts: [],
      delid: 98,
    };
  },
  methods: {
    savePost() {
      const data = {
        title: this.post.title,
        body: this.post.body,
        userId: this.post.userId,
      };
      PostDataService.create(data)
        .then((Response) => {
          this.post.id = Response.data.id;
          console.log(Response.data.id);
          this.currentPost = Response.data;
          console.log(this.currentPost.data);
          this.currentPostid = Response.data.id;
        })
        .catch((e) => {
          console.log(e);
        });
    },
    getPost() {
      PostDataService.getAll()
        .then((response) => {
          this.tenders = response.data;
          console.log(response.data);
          this.posts = response.data;
        })
        .catch((e) => {
          console.log(e);
        });
    },
    updatepost() {
      PostDataService.update(98, this.post)

        .then((response) => {
          console.log(response.data);
        })
        .catch((e) => {
          console.log(e);
        });
    },
    deletePost() {
      PostDataService.delete(this.delid)
        .then((response) => {
          console.log(response.data);
        })
        .catch((e) => {
          console.log(e);
        });
    },
  },
};
</script>

<style>
</style>
