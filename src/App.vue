<script setup>
  import BlogPost from './components/BlogPost.vue';
  import {ref} from "vue";

  const posts = ref([]);
  const favorito = ref('');

  const cambiarFavorito = (title) => {
    favorito.value = title;
  }

  fetch('https://jsonplaceholder.typicode.com/posts')
      .then(response => response.json())
      .then(json => posts.value = json)

</script>
<template>
  <div class="container">
    <h1>Posts</h1>
    <h2>My favorite posts: {{favorito}}</h2>
    <BlogPost 
      v-for="post in posts"
      :key = "post.id"
      :id="post.id"
      :title="post.title"
      :body="post.body"
      :cambiarFavorito="cambiarFavorito"
    />
  </div>
</template>