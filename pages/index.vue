<template>
  <div>
    <div v-for="hero in heroes"
        v-if="hero.image"
        id="hero"
        class=" uk-section uk-height-small uk-flex uk-flex-center uk-flex-middle uk-background-cover uk-light uk-padding"
        :data-src="hero.image.url"
        uk-img>
      >
      <div>
        <h1>
          {{hero.title}}
        </h1>
        <br/>
        <div >
          <button class="uk-button uk-button-primary uk-align-center">{{ hero.button }}</button>
        </div>
      </div>
    </div>
    <div class="uk-section">
      <div class="uk-container uk-container-large">
        <Articles :articles="articles"></Articles>
      </div>
    </div>

  </div>
</template>

<script>
import articlesQuery from '~/apollo/queries/article/articles'
import heroQuery from '~/apollo/queries/hero/heroes'
import Articles from '~/components/Articles'

export default {
  data() {
    return {
      articles: [],
      heroes: []
    }
  },
  components: {
    Articles
  },
  apollo: {
    articles: {
      prefetch: true,
      query: articlesQuery,
      variables () {
        return { id: parseInt(this.$route.params.id) }
      }
    },
    category: {
      prefetch: true,
      query: articlesQuery,
      variables () {
        return { id: parseInt(this.$route.params.id) }
      }
    },
    heroes: {
      prefetch: true,
      query: heroQuery,
      variables () {
        return { id: parseInt(this.$route.params.id) }
      }
    }
  }
}
</script>
