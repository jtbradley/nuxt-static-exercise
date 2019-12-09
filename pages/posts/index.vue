<template>
  <div>
    <h2>Making API Request -  The Vue Way</h2>

    <div class="container row">
      <Card v-for="post in posts" :key="post.id" :post="post" class="mx-auto" />
      <button class="btn btn-danger" v-scroll-to="'body'">Back to Top</button>
    </div>

  </div>
</template>

<script>
import axios from 'axios'
import Card from '@/components/card'
import {mapGetters} from 'vuex'

export default {
  components: {
    Card
  },
  data() {
    return {
      allPosts: ''
    }
  },
  computed: {
    ...mapGetters(['posts'])
    /*
    allPosts(){
      // Don't need map getter w this
      return this.$store.getters.posts
    }
    */
  },
  async fetch({store}){
    let {data} = await axios.get('https://jsonplaceholder.typicode.com/posts')
    store.dispatch('setPosts', data)
  },

  /*
  async asyncData({store}){
    let {data} = await axios.get('https://jsonplaceholder.typicode.com/posts')
    //return {allPosts: data}
    store.dispatch('setPosts', data)
  },*/
  head: {
    title: 'List of Posts'
  }
}
</script>

<!--
<script>
import axios from 'axios'
export default {
  data() {
    return {
      posts: ''
    }
  },
  asyncData(){
    // The Nuxt Way
    return axios.get('https://jsonplaceholder.typicode.com/todos')
    .then(res => {
      //console.log(res)
      return {posts: res.data}
    })
  }
}
</script>-->

<!--<script>
import axios from 'axios'
export default {
  data(){
    return {
      posts: []
    }
  },
  mounted() {
    // The Vue way
    axios.get('https://jsonplaceholder.typicode.com/todos')
    .then(response => {
      this.posts = response.data;
      console.log(response);
    })
    .catch(error => {
      console.log(error);
    })
  }
}
</script>-->
