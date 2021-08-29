<template>
  <div class="flex flex-column align-start align-self-start justify-start">
    <h1>Welcome to your dashboard</h1>
    <p>You are now logged in {{ $nuxt.$fire.auth.currentUser.email }}</p>
    <v-btn @click="$router.push('/auth/signout')">Logout</v-btn>
    <v-btn color="black" dark large @click="$fetch">
      Another &nbsp; <v-icon>refresh</v-icon>
    </v-btn>
    <!-- <img :src="cats.data.images.original.url" alt="" /> -->

    <!-- 
          <img :src="cats.data.images.original.url" alt="" />
              <img :src="cats.data.images.original.url" alt="" />

<v-layout row wrap>
      <v-flex xs12>
        <v-card flat tile class="d-flex">
          <v-img :src="image.url" contain> </v-img>
        </v-card>
      </v-flex>
    </v-layout> -->
  </div>
</template>

<script>
export default {
  data() {
    return {
      cats: []
    };
  },
  activated() {
    if (this.$fetchState.timestamp <= Date.now() - 30000) {
      this.$fetch();
    }
  },

  async fetch() {
    const cats = await this.$axios.$get(
      "https://api.giphy.com/v1/gifs/translate?api_key=ShwQz1yuFlZwCalQ6bPu2O53jS1GC80E&s=cats"
    );

    console.log(cats.data.images.original.url);
    return { cats };
  }
  // async asyncData({ $axios }) {
  //   const cats = await $axios.$get(
  //     "https://api.giphy.com/v1/gifs/translate?api_key=ShwQz1yuFlZwCalQ6bPu2O53jS1GC80E&s=cats"
  //   );
  //   console.log(cats.data.images.original.url);
  //   const catsData = await response.json();
  //   console.log(catsData.data.images.original.url);

  //   return { catsData };
  // }
};
</script>
// f845d322-d851-40ee-9dcd-aac32e21ddbbs
