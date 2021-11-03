<template>
  <div>
    <v-container>
      <v-flex xs12 pb-5>
        <h1>News</h1>
      </v-flex>

      <v-flex>
        <v-flex
          xs12
          sm6
          offset-sm3
          pb-3
          v-for="(article, index) in articles"
          :key="index"
        >
          <v-card>
            <img
              class="white--text align-end"
              height="200px"
              width="100"
              :src="article.urlToImage"
            />

            <v-card-subtitle class="pb-0">
              {{ article.title }}
            </v-card-subtitle>

            <v-card-text class="text--primary">
              <div>{{ article.content }}</div>
            </v-card-text>

            <v-card-actions>
              <v-btn color="orange" text flat :href="article.url" target="_blank"> Explore </v-btn>
            </v-card-actions>
          </v-card>
        </v-flex>
      </v-flex>
    </v-container>
  </div>
</template>

<script>
export default {
  async asyncData({ app }) {
    const { articles } = await app.$axios.$get(
      "https://newsapi.org/v2/everything?q=tesla&from=2021-10-03&sortBy=publishedAt&apiKey=ee346198c2d44fd6870f5b8fb21a25ba"
    );
    return { articles };
  },
};
</script>

<style>
</style>
