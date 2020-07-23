<template>
  <PostLayout>
    <h1 class="tag-title text-center space-bottom">
      # {{ $page.tag.title }}
    </h1>

    <div class="posts">
      <PostCard v-for="edge in $page.posts.edges" :key="edge.node.id" :post="edge.node"/>
    </div>
  </PostLayout>
</template>

<page-query>
query Tag ($id: ID!) {
  tag:  tag(id: $id) {
    title
    # belongsTo(filter: {}) {
    #   edges {
    #     node {
    #       ...on Post {
    #         title
    #         path
    #         date (format: "D. MMMM YYYY")
    #         timeToRead
    #         description
    #         content
    #       }
    #     }
    #   }
    # }
  }
  # I found out that the above can't be filtered and I fiddled wih this until I got it right myself, the tags are a many relation
  # https://github.com/gridsome/gridsome/issues/556
  posts: allPost(filter: { tags: {id: { eq: $id}} , published: { eq: true } }) {
    edges {
      node {
        title
        path
        date (format: "D. MMMM YYYY")
        timeToRead
        description
        content
      }
    }
  }
}
</page-query>

<script>
import Author from '~/components/Author.vue'
import PostCard from '~/components/PostCard.vue'
import PostLayout from '~/layouts/PostLayout.vue'

export default {
  components: {
    Author,
    PostCard,
    PostLayout
  },
  metaInfo: {
    title: 'Hello, world!'
  }
}
</script>

<style lang="scss">

</style>

