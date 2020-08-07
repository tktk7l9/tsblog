<template>
  <div>
    <navbar />
    <section class="container">
      <div class="columns is-mobile">
        <div class="column main-page-contents">
          <nuxt />
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";

export default {
  components: {
    Navbar,
  },
};
</script>

<style scoped>
#body-contents {
  margin-top: 2em;
}
</style>
