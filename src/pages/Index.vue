<template>
  <Layout>
    <h1>Дописи</h1>

    <div v-for="edge in $page.posts.edges" :key="edge.node.id">
      <g-link :to="edge.node.path" class="post-preview__title-link">
        <h2 class="post-preview__title" v-html="edge.node.title"></h2>
      </g-link>
      <small class="post-preview__date-mark">
        {{ new Date(edge.node.date).toLocaleDateString('uk-UA', {
    year: 'numeric',
    month: 'long',
    day: 'numeric',
  }) }} &mdash;
  <ReadingTime :time="edge.node.timeToRead" />
      </small>
      <p class="post-preview__description" v-html="edge.node.description" />
      <br /><br />
    </div>
  </Layout>
</template>

<page-query>
query {
  posts: allMarkdownPost {
    edges {
      node {
        id
        title
        date
        timeToRead
        description
        path
      }
    }
  }
}
</page-query>

<script>
import ReadingTime from '@/components/ReadingTime.vue';

export default {
  components: {
    ReadingTime,
  },
  metaInfo: {
    title: 'Hello, world!',
  },
};
</script>
