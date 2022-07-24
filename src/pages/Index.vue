<template>
  <Layout>

    <article v-for="post in $page.posts.edges" :key="post.id" >
      {{ post }}
      <br>
      <br>
      <br>
      <br>
      ==== {{ $page }}
    </article>

  </Layout>
</template>

<page-query>
query Posts ($page: Int) {
  posts: allPost (sortBy: "date", order: DESC, perPage: 10, page: $page) @paginate {
    totalCount
    pageInfo {
      totalPages
      currentPage
    }
    edges {
      node {
        id
        title
        date (format: "MMMM D, Y")
        summary
        path
      }
    }
  }
}
</page-query>

<script>
export default {
  metaInfo: {
    title: 'Hello, world!'
  }
}
</script>

<style>
  .home-links a {
    margin-right: 1rem;
  }
</style>
