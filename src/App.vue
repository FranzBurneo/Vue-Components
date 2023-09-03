<script setup>
  import BlogPost from './components/BlogPost.vue';
  import {ref, computed} from "vue";
  import PaginatePost from './components/PaginatePost.vue';
  import LoadingSpinner from './components/LoadingSpinner.vue'

  const posts = ref([]);
  const favorito = ref('');
  const postXpage = 10;
  const inicio = ref(0);
  const fin = ref(postXpage);
  const loading = ref(false);

  const cambiarFavorito = (title) => {
    favorito.value = title;
  }

  const next = () => {
    inicio.value += postXpage;
    fin.value += postXpage;
  }
  const previus = () => {
    inicio.value += - postXpage;
    fin.value += - postXpage;
  }

  fetch('https://jsonplaceholder.typicode.com/posts')
      .then(response => response.json())
      .then(json => posts.value = json)

  const maxLength = computed(() => posts.value.length)

</script>
<template>
  <LoadingSpinner v-if="loading" />
  <div class="container" v-else>
    <h1>Posts</h1>
    <h2>My favorite posts: {{favorito}}</h2>
    <PaginatePost class="mb-2"
      @previus = "previus"
      @next = "next"
      :inicio="inicio"
      :fin="fin"
      :maxLength="maxLength"
    />
    <BlogPost 
      v-for="post in posts.slice(inicio, fin)"
      :key = "post.id"
      :id="post.id"
      :title="post.title"
      :body="post.body"
      :cambiarFavorito="cambiarFavorito"
      class="mb-2"
    />
  </div>
</template>