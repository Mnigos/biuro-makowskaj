<template>
  <v-main>
    <div v-for="post in posts" :key="post.title">
      <BlogPost
        :title="post.title"
        :image="post.image"
        :description="post.description"
        :date="post.date"
      />
    </div>
  </v-main>
</template>

<script lang="ts">
import Vue from 'vue';
import BlogPost from '../../components/BlogPost.vue';

export default Vue.extend({
  components: {
    BlogPost,
  },
  async asyncData({ $content }: any) {
    const articles = await $content('articles').fetch();

    return {
      posts: articles,
    };
  },
});
</script>
