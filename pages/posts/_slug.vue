<template>
  <div>
    <h1 class="title">
      {{ post.fields.title }}
    </h1>
    <div class="has-text-right">
      <p>
        <small>{{ $getFormattedDate(post.fields.publishedAt) }}</small>
      </p>
    </div>
    <hr />
    <div>
      {{ post.fields.body }}
    </div>
  </div>
</template>

<script>
import { mapState } from "vuex";

export default {
  computed: {
    ...mapState(["posts"]),
    post() {
      return this.posts.find(
        (post) => post.fields.slug === this.$route.params.slug
      );
    },
  },
};
</script>

<style></style>
