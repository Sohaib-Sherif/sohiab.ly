<template>
  <PostLayout>
    <div class="post-title">
      <h1 class="post-title__text">
        {{ $page.post.title }}
      </h1>

      <PostMeta :post="$page.post" />
      <PostTags :post="$page.post" />


    </div>

    <div class="post content-box content-box__post">
      <div class="post__header">
        <!-- <g-image alt="Cover image" v-if="$page.post.cover_image" :src="$page.post.cover_image" />
         -->
         <!-- <cld-image
        cloudName="mrdestiny"
        :publicId="getPath($page.post.cover_image)"
        loading="lazy">
          <cld-transformation width="1000" height="300" fetchFormat="auto" crop="fill" gravity="auto"/>
          <cld-placeholder>
          </cld-placeholder>
        </cld-image> -->
        <lazy-image
        :src="getPath($page.post.cover_image)"
        :src-placeholder="getPath($page.post.cover_image, true)"
        >

        </lazy-image>
      </div>

      <div class="post__content" v-html="$page.post.content" />

      <!-- <div class="post__footer">
        <PostTags :post="$page.post" />
      </div> -->
    </div>

    <div class="post-comments">
      <!-- Add comment widgets here -->
    </div>
    <!-- <Author class="post-author" /> -->
  </PostLayout>
</template>

<script>
import PostMeta from '~/components/PostMeta'
import PostTags from '~/components/PostTags'
import Author from '~/components/Author.vue'
import PostLayout from '~/layouts/PostLayout.vue'
import LazyImage from 'v-lazy-image'

export default {
  components: {
    Author,
    PostMeta,
    PostTags,
    PostLayout,
    LazyImage
  },
  metaInfo () {
    return {
      title: this.$page.post.title,
      meta: [
        {
          name: 'description',
          content: this.$page.post.description
        }
      ]
    }
  },
  methods: {
    getPath(path, placeholder) {
      let sections = path.split('/');
      let lastSection = sections[sections.length - 1]
      let base_url = ""
      if(placeholder) {
        base_url = "https://res.cloudinary.com/mrdestiny/image/upload/c_fill,g_auto,f_auto,ar_10:4,q_1,e_blur:1000/"
      }
      else {
        base_url = "https://res.cloudinary.com/mrdestiny/image/upload/c_fill,g_auto,f_auto,ar_10:4/"
      }
      return base_url + lastSection;
    }
  }
}
</script>

<page-query>
query Post ($id: ID!) {
  post: post (id: $id) {
    title
    path
    date (format: "D. MMMM YYYY")
    timeToRead
    tags {
      id
      title
      path
    }
    description
    content
    cover_image
  }
}
</page-query>

<style lang="scss">
.content-box__post {
  //override some content box values here instead of the global file
	max-width: calc(var(--content-width) + 10em);
  margin: 0 auto;
  padding: 0;
  width: 100%;;
}

.post-title {
  padding: calc(var(--space) / 2) 0 calc(var(--space) / 2);
  text-align: center;
}

.post {

  &__header {
    // width: calc(100% + var(--space) * 2);
    // margin-left: calc(var(--space) * -1);
    // margin-top: calc(var(--space) * -1);
    margin-bottom: calc(var(--space) / 2);
    overflow: hidden;
    border-radius: var(--radius) var(--radius) 0 0;

    

    img {
      width: 100%;
    }

    &:empty {
      display: none;
    }
  }

  &__content {
    @media screen and (max-width: 650px) {
			padding: 0 var(--space);
		}
    padding: 0 calc(var(--space) - 2em);
    h2:first-child {
      margin-top: 0;
    }

    p:first-of-type {
      font-size: 1.2em;
      color: var(--title-color);
    }

    img {
      width: calc(100% + var(--space) * 2);
      margin-left: calc(var(--space) * -1);
      display: block;
      max-width: none;
    }
  }

  &__footer {
      padding: 0  calc(var(--space) - 2em) calc(var(--space) - 2em);
    }
}

.post-comments {
  padding: calc(var(--space) / 2);

  &:empty {
    display: none;
  }
}

.post-author {
  margin-top: calc(var(--space) / 2);
}
</style>
