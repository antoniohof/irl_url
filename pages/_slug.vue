<template>
  <div>
    <div class='back'>
      <NuxtLink to="/">back</NuxtLink>
    </div>
    <h2>{{ post.title }}</h2>
    <nuxt-content :document="post" />
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params, error }) {
    let post;
    try {
      post = await $content("posts", params.slug).fetch();
      // OR const article = await $content(`articles/${params.slug}`).fetch()
    } catch (e) {
      error({ message: "Posts not found" });
    }

    return {
      post,
    };
  },
}
</script>

<style scoped>
* {
	font-family: 'Roboto Mono', monospace !important;
}
</style>