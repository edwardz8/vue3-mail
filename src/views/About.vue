<template>
  <div class="about">
    <h1>This is an about page</h1>
    

    <div v-for="article in articles.articles" :key="article.title">
      <img :src="article.urlToImage" width="300" />
      <div>{{article.title}}</div>
      <div>{{article.author}}</div>
    </div>

  </div>
</template>


<script>
import { ref, onBeforeMount } from 'vue'

export default {
  setup() {
    const articles = ref([])

    const fetchArticles = async () => {
      try {
        const response = await fetch('https://newsapi.org/v2/everything?domains=nfl.com&apiKey=62047a955ea94cc094e50c43ede1703f')
        const parsedResponse = await response.json()

        articles.value = parsedResponse
        console.log(parsedResponse)
      } catch(err) {
        console.log(err)
      }
    }

    onBeforeMount(() => {
      fetchArticles()
    })

    return {
      articles
    }
  }
};
</script>