<template>
  <div>
    <card v-for="(post, index) in posts" :key="index" :post="post" />
  </div>
</template>

<script>
import Card from "@/components/Card.vue";
import sdkClient from "@/plugins/contentful.js";

export default {
  components: {
    Card,
  },
  async asyncData({ env }) {
    let posts = [];
    await sdkClient
      .getEntries({
        content_type: "blogPost",
        order: "-fields.publishedAt",
      })
      .then((res) => {
        posts = res.items;
      })
      .catch(console.error);
    return { posts };
  },
};
</script>
