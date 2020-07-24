<template>
  <div class="post-card content-box" :class="{'post-card--has-poster' : post.poster}">
    <div class="post-card__header">
      <!-- <g-image alt="Cover image" v-if="post.cover_image" class="post-card__image" :src="post.cover_image" /> -->
      <!-- <cld-image
        v-if="post.cover_image"
        cloudName="mrdestiny"
        :publicId="getPath(post.cover_image)"
        loading="lazy"
        alt="cover image"
        >
          <cld-transformation width="1000" height="300" fetchFormat="auto" crop="fill" gravity="auto"/>
          <cld-placeholder>
          </cld-placeholder>
        </cld-image> -->
    </div>
    <div class="post-card__content">
      <h2 class="post-card__title" v-html="post.title" />
      <p class="post-card__description" v-html="post.description" />

      <PostMeta class="post-card__meta" :post="post" />
      <PostTags class="post-card__tags" :post="post" />

      <g-link class="post-card__link" :to="post.path">Link</g-link>
    </div>
  </div>
</template>

<script>
import PostMeta from '~/components/PostMeta'
import PostTags from '~/components/PostTags'
// import {CldImage, CldTransformation, CldPlaceholder} from 'cloudinary-vue'

export default {
  components: {
    PostMeta,
    PostTags,
    // CldImage,
    // CldTransformation,
    // CldPlaceholder
  },
  props: ['post'],
  methods: {
    getPath(path) {
      let sections = path.split('/');
      let lastSection = sections[sections.length - 1]
      return lastSection;
    }
  }
}
</script>

<style lang="scss">
.post-card {
  margin-bottom: var(--space);
  position: relative;

  &__header {
    margin-left: calc(var(--space) * -1);
    margin-right: calc(var(--space) * -1);
    margin-bottom: calc(var(--space) / 2);
    margin-top: calc(var(--space) * -1);
    overflow: hidden;
    border-radius: var(--radius) var(--radius) 0 0;
    padding: calc(var(--space) - 1.5em) calc(var(--space) - 1.5em) 0 calc(var(--space) - 1.5em);

    &:empty {
      display: none;
    }
  }

  &__image {
    min-width: 100%;
  }

  &__title {
    margin-top: 0;
  }

  &:hover {
    transform: translateY(-5px);
    box-shadow: 1px 10px 30px 0 rgba(0,0,0,.1);
  }

  &__tags {
    z-index: 1;
    position: relative;
  }

  &__link {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    opacity: 0.0;
    overflow: hidden;
    text-indent: -9999px;
    z-index: 0;
  }
}
</style>
