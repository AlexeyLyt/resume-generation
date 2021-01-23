<template>
  <div class="container">
    <p v-if="!comments">
      <button class="btn primary" @click="getComments">Загрузить комментарии</button>
    </p>
    <div v-if="comments && !loading" class="card">
      <h2>Комментарии</h2>
      <FeedbackList v-for="comment in comments" :key="comment.id" :comment="comment" />
    </div>
  </div>
  <div v-if="loading" class="loader"></div>
</template>

<script>
import axios from 'axios'
import FeedbackList from '@/components/FeedbackList.vue'
export default {
  components: { FeedbackList },
  data: () => ({
    comments: null,
    loading: false
  }),
  methods: {
    getComments() {
      this.loading = true
      this.comments = []
      setTimeout(async () => {
        try {
          const {data} = await axios.get('https://jsonplaceholder.typicode.com/comments?_limit=42')
          this.comments = data
          this.loading = false
        } catch(e) {
          this.loading = false
        }
      }, 250);
    }
  }
};
</script>

<style></style>
