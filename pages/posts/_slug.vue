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
  },
  async asyncData({ payload, store, params, error }) {
    const post =
      payload ||
      (await store.state.posts.find(
        (post) => post.fields.slug === params.slug
      ));
    if (post) {
      return { post };
    } else {
      return error({
        statusCode: "404",
        message: "お探しのページは見つかりませんでした",
      });
    }
  },
};
</script>

<style></style>
