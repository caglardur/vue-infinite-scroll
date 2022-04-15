<template>
  <v-col sm="12" md="6" lg="4" class="d-flex align-center ma-0 pa-0 mx-auto">
    <ul>
      <li v-for="(post, index) in posts" :key="index">
        <div class="card">
          <header class="card-header">
            <p class="card-header-title">
              {{ post.title }}
            </p>
          </header>
          <div class="card-content">
            <div class="content">
              <p>{{ post.body }}</p>
            </div>
          </div>
        </div>
      </li>
    </ul>
  </v-col>
</template>

<script lang="ts">
import Vue from "vue"
import axios from "axios"

interface itemType {
  body: string
  id: number
  title: string
  userId: number
}

export default Vue.extend({
  name: "HomeView",

  components: {},
  data: () => ({
    posts: new Array<itemType>(),
    page: 0
  }),
  methods: {
    getData() {
      axios.get(`https://jsonplaceholder.typicode.com/posts`).then(response => {
        if (response.data) {
          if (this.posts.length === 0) {
            this.posts = response.data.slice(this.page * 10, (this.page + 1) * 10)
          } else {
            let sliceData: itemType = response.data.slice(this.page * 10, (this.page + 1) * 10)
            this.posts = this.posts.concat(sliceData)
          }
        }
      })
    },
    scrollHandle() {
      if (window.innerHeight + document.documentElement.scrollTop == document.documentElement.offsetHeight) {
        this.page += 1
        this.getData()
      }
    }
  },
  created() {
    window.addEventListener("scroll", this.scrollHandle)
    this.getData()
  },
  watch: {
    scrollTop() {
      this.getData()
    },
    page() {
      this.getData()
      console.log(this.page)
    }
  }
})
</script>
<style scoped>
li {
  margin-bottom: 1rem;
}
</style>
