<template>
  <div>
    <div class="hero">
      <div class="container">
        <h1>Welcome to My Blog</h1>
        <p class="subtitle">Lorem, ipsum dolor sit amet consectetur adipisicing elit. Commodi, modi. Maxime explicabo neque odio facilis.</p>
        <nuxt-link to="/contact" class="hire">Hire me</nuxt-link>
      </div>
    </div>

    <div class="container">
      <main>
        <h2>Latest thoughts</h2>
        <ul>
          <li v-for="(post, index) in posts" :key="index">
            <img :src="post.feature_image">
            <div class="content">
              <span>{{ post.authors[0].name }}</span>
              <nuxt-link :to="{ path: post.slug }">{{ post.title }}</nuxt-link>
              <p>{{ post.excerpt }}</p>
            </div>
          </li>
        </ul>
      </main>
    </div>

  </div>
</template>

<script>

import { getPosts } from '~/api/posts';

export default {
  async asyncData () {
    const posts = await getPosts();
    return { posts: posts }
  }
}
</script>

<style>

.hero {
  background-color: purple;
  color: white;
  text-align: center;
  padding-top: 2em;
}
.hero h1 {
  margin-bottom: 1em;
}
.hero .hire {
  background: #4d004d;
  padding: 0.5em 3em;
  margin: 2em 0 3em;
  display: inline-block;
  border-radius: 10px;
  color: gray;
  text-decoration: none;
}
.container ul {
  list-style-type: none;
  padding: 0;
}
main li {
  background: white;
  border-radius: 1em;
  padding: 0.8em;
  margin: 1em 0;
  box-shadow: 15px 21px 40px 0px rgba(0, 0, 0, 0.04);
}
main img {
  width: 100%;
  border-radius: 0.5em;
}
main .content {
  padding: 0.5em;
}
main a {
  font-size: 1.5em;
  text-decoration: none;
  color: black;
  font-weight: bold;
  display: block;
  margin: -0.1em 0 0.2em;
}
main h2 {
  margin-top: 3em;
  text-transform: uppercase;
  font-size: 0.8em;
}
main span {
  color: purple;
  text-transform: uppercase;
}
@media only screen and (min-width: 768px) {
  main li {
    display: grid;
    grid-template-columns: 180px auto;
    grid-column-gap: 1em;
  }
}


  

</style>
