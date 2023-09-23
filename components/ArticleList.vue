<template>
  <div>
    <h1>Daftar Artikel</h1>
    <ul>
      <li v-for="(article, index) in articles" :key="index">
        <nuxt-link class="nav-link active" aria-current="page" :to="'/app/detail/' + index">{{ article.title }}</nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    articles: Array,
  },
};
</script>

<style>
  li:hover {
    color: skyblue;
    transition-duration: 100ms;
  }
</style>