<template>
  <div>
    <div class="card" style="width: 18rem;">
      <div class="card-header">{{ post.id }}</div>
  <div class="card-body">
    <h5 class="card-title" >{{ post.title }}</h5>
    <nuxt-link :to="{name: 'posts-id', params: {id: post.id}}" class="card-link">Read Post</nuxt-link>
  </div>
</div>
  </div>
</template>

<script>
export default {
  props: {
    post: Object
  }
}
</script>
