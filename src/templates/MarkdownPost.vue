
<template>
  <Layout>
    <h1 class="title">{{ $page.post.title }}</h1>
    <em>{{ $page.post.date }}</em>
    <div class="content" v-html="$page.post.content" />

    <div class="post-comments">
<!--      <vue-disqus-->
<!--          shortname="DISQUSSHORTNAME"-->
<!--          :identifier="$page.post.title"-->
<!--      ></vue-disqus>-->
    </div>
  </Layout>
</template>

<script>
export default {
  metaInfo() {
    return {
      title: this.$page.post.title,
      meta: [
        {
          name: "description",
          content: this.$page.post.description,
        },
      ],
    };
  },
};
</script>

<page-query>
query MarkdownPost ($id: ID!) {
  post: markdownPost (id: $id) {
    title
    path
    date
    description
    content
  }
}
</page-query>
