
<template>
  <div>
    <v-container>
      <h1 class="mb-5">記事一覧</h1>
      <div v-for="(article, index) in articles" :key="index">
        <article-card :article="article"></article-card>
      </div>
    </v-container>
  </div>
</template>

<script>
import axios from "axios";
import ArticleCard from "../components/ArticleCard.vue";
export default {
  components: {
    ArticleCard,
  },

  data() {
    return {
      articles: {},
    };
  },
  methods: {
    async getArticles() {
      const res = await axios.get("http://localhost:8080/articles");
      this.articles = res.data;
    },
  },

  mounted() {
    this.getArticles();
  },
};
</script>
