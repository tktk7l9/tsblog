<template>
  <div>
    <card v-for="(post, index) in posts" :key="index" :post="post" />
  </div>
</template>

<script>
import Card from "@/components/Card.vue";
import { mapState } from "vuex";

export default {
  components: {
    Card,
  },
  computed: {
    ...mapState(["posts"]),
  },
};
</script>
