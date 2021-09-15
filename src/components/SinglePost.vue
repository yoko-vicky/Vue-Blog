<template>
  <router-link :to="{ name: 'Details', params: { id: post.id } }">
    <h3>{{ post.title }}</h3>
  </router-link>
  <p>{{ snippet }}</p>
  <span v-for="tag in post.tags" :key="tag">
    #{{ tag }}
  </span>
</template>

<script>
import { computed } from '@vue/reactivity'
export default {
  name: 'SinglePost',
  props: ['post'],
  setup(props){
    const snippet = computed(()=>{
      return props.post.body.substring(0, 100) + '...'
    })

    return {
      snippet
    }
  }
}
</script>

<style>

</style>
