<template>
  <Layout>
    <div class="container">
      <h1 class="title">Sid's Gridsome Blog</h1>
      <div v-for="article in $page.articles.edges" :key="article.id" class="article d-flex">
        <div class="article__img"
             :style="{ 'background-image': 'url(' + article.node.image + ')' }"></div>
        <div class="article__body">
          <g-link :to="article.node.path" class="article__link"></g-link>
          <h2 class="article__title">{{article.node.title}}</h2>
          <p class="article__abstract">{{article.node.abstract | shorten}}</p>
          <p class="article__pub_ttr">{{article.node.date | striptime}} - {{article.node.timetoread}} read</p>
        </div>
      </div>
    </div>
  </Layout>
</template>
<page-query>
query {
  articles: allArticles {
    edges {
      node {
        title
        abstract
        date
        timetoread
        image
        path
      }
    }
  }
}
</page-query>
<script>
export default {
  filters: {
    shorten: function(value) {
      if (value.length > 50) {
        return value.slice(0, 50) + '...';
      }
        return value;
    },
    striptime: function(value) {
      return value.slice(0,value.indexOf('T'));
    }
  },
  metaInfo: {
    title: "My blog"
  }
};
</script>
<style>
.article {
  display: flex;
  align-items: center;
  box-shadow: 5px 5px 11px rgba(0, 0, 0, 0.15);
  border-radius: 8px;
  position: relative;
  margin-top: 50px;
  background-color: #fff;
}
@media screen and (max-width: 992px) {
  .article {
    display: block;
    margin: 28px;
  }
  .title {
    margin: 28px;
  }
}
.article__title {
  margin-top: 0;
}
.article__body {
  padding: 15px 30px;
}
.article__link {
  position: absolute;
  top: 0;
  right: 0;
  left: 0; 
  bottom: 0;
}
.article__img {
  width: 250px;
  height: 170px; 
  background-size: cover;
  background-position: center;
  border-radius: 8px;
  margin-right: 15px;
}

@media screen and (max-width: 992px) {
  .article__img {
    width: 100%;
    height: 180px;
  }
  .article__abstract{
   min-width: 0;
  }
  .article__pub_ttr{
    font-size: 0.8rem;
  }
}
</style>