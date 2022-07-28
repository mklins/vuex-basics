<script>
import { mapGetters, mapActions } from 'vuex'
import PostForm from './components/PostForm.vue'
export default {
  /* computed: {
    allPosts() {
      return this.$store.getters.allPosts
    }
  }, */
  computed: mapGetters(['validPosts', 'postsCount']),
  methods: mapActions(['fetchPosts']),
  components: { PostForm },
  async mounted() {
    //this.$store.dispatch('fetchPosts')
    this.fetchPosts(4);
  }
}
</script>

<template>
  <main>
    <PostForm />
    <h1>{{ postsCount }}</h1>
    <div class="post" v-for="post in validPosts" :key="post.id">
      <h2>{{ post.title }}</h2>
      <p>{{ post.body }}</p>
    </div>
  </main>
</template>

<style scoped>
main {
  text-align: center;
  margin: 60px auto;
  width: 400px;
}

.post {
  border: 1px solid #ccc;
  border-radius: 5px;
  margin-bottom: 1rem;
}
</style>
