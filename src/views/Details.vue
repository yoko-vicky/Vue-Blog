<template>
  <div v-if="error">{{ error }}</div>
  <div v-if="post" class="post">
    <h3>{{ post.title }}</h3>
    <p class="pre">{{ post.body }}</p>
    <!-- <div v-if=""></div> -->
  </div>
</template>

<script>
import getPost from '../composables/getPost'

export default {
  name: 'Details',
  props: ['id'],
  setup(props){
    const { post, error, load } = getPost(props.id)
    load()

    return {
      post, error
    }
  }
}
</script>

<style scoped>
  .tags a {
    margin-right: 10px;
  }
  .post {
    max-width: 1200px;
    margin: 0 auto;
  }
  .post p {
    color: #444;
    line-height: 1.5em;
    margin-top: 40px;
  }
  .pre {
    white-space: pre-wrap;
  }
</style>
