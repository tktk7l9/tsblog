<template>
  <div class="box is-radiusless">
    <nuxt-link :to="linkTo(post)">
      <article class="media">
        <figure class="media-left">
          <div v-if="post.fields.headerImage">
            <p class="image is-128x128">
              <img
                :src="post.fields.headerImage.fields.file.url"
                alt="thumbnail"
              />
            </p>
          </div>
          <div v-else>
            <p class="image is-128x128">
              <img
                src="https://bulma.io/images/placeholders/128x128.png"
                alt="thumbnail"
              />
            </p>
          </div>
        </figure>
        <figure class="media-content">
          <div class="content">
            <div class="is-size-4">
              {{ post.fields.title }}
            </div>
            <div class="has-text-right">
              <small>{{ $getFormattedDate(post.fields.publishedAt) }}</small>
            </div>
          </div>
        </figure>
      </article>
    </nuxt-link>
  </div>
</template>

<script>
export default {
  props: {
    post: {
      type: Object,
      reqire: true,
      default: () => {
        return {
          fields: {
            title: "sample",
            publishedAt: new Date(),
            headerImage: null,
          },
        };
      },
    },
  },
  methods: {
    linkTo(post) {
      return { name: "posts-slug", params: { slug: post.fields.slug } };
    },
  },
};
</script>

<style scoped>
.box {
  box-shadow: 0.5em;
  margin-bottom: 10px;
}
</style>
