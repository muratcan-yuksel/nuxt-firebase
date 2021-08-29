<template>
  <div class="flex flex-column align-start align-self-start justify-start">
    <h1>Welcome to your dashboard</h1>
    <p>You are now logged in {{ $nuxt.$fire.auth.currentUser.email }}</p>
    <v-btn @click="$router.push('/auth/signout')">Logout</v-btn>
    <v-btn color="black" dark large @click="fetch">
      Another &nbsp; <v-icon>refresh</v-icon>
    </v-btn>
    <!-- <img :src="cats.data.images.original.url" alt="" /> -->
    <img src="https://api.giphy.com/v1/gifs/translate?api_key=ShwQz1yuFlZwCalQ6bPu2O53jS1GC80E&s=cats" id="images" alt="" />
  
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      cats: []
    };
  },

  methods: {
    fetch: async function sth() {
      const api =
        "https://api.giphy.com/v1/gifs/translate?api_key=ShwQz1yuFlZwCalQ6bPu2O53jS1GC80E&s=cats";
      const cats = await axios.get(api).then(response => {
        return response.data;
      });
      console.log(cats.data.images.original.url);
      document.getElementById("images").src = cats.data.images.original.url;
      return { cats };
    }
  },

  window.onload= fetch


};
</script>
// f845d322-d851-40ee-9dcd-aac32e21ddbbs
