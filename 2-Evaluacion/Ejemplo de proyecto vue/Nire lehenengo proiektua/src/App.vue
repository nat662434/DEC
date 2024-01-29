<!-- <script setup>
  import ButtonCounter from './components/ButtonCounter.vue';
  import Post from './components/Post.vue';
  import "bootstrap/dist/css/bootstrap.css";

  import {ref} from "vue";
  const posts = ref ([
    {title: "post 1", id: 1, body: "decsripcion 1"},
    {title: "post 2", id: 2, body: "decsripcion 2"},
    {title: "post 3", id: 3, body: "decsripcion 3"},
    {title: "post 4", id: 4}
  ]);
</script>

<template>
  <div class="container">
    <h1>Nire lehenengo proiektua</h1>
    <ButtonCounter />
    <ButtonCounter />
    <ButtonCounter />

    <Post title ="Post 1" id="1" body="descripcion 1" colorText="primary"/>
    <Post title ="Post 2" id="2" body="descripcion 2" colorText="secondary"/>
    <Post title ="Post 3" id="3" body="descripcion 3" colorText="primary"/>
    <Post title ="Post 4" id="4" body="descripcion 4" colorText="primary"/>
  </div>
</template> -->

<!-- <style>
</style> -->
<script setup>
import ButtonCounter from "./components/ButtonCounter.vue";
import "bootstrap/dist/css/bootstrap.css";
import BlogPost from "./components/BlogPost.vue";
import PaginatePost from "./components/PaginatePost.vue";
import { ref } from "vue";  // para que sea reactivo

const favorito = ref("");
const cambiarFavorito = (title) => {
  favorito.value = title;
};

const posts = ref([]);
const postXpage = 10;
const inicio = ref(0);
const fin = ref(postXpage);

fetch("https://jsonplaceholder.typicode.com/posts")
  .then((res) => res.json())
  .then((data) => (posts.value = data));

// Metodo next
const next = () => {
  inicio.value += postXpage;
  fin.value += postXpage;
};

const prev = () => {
  inicio.value -= postXpage;
  fin.value -= postXpage;
};

// const posts = ref([
//     { title: "post 1", id:1, body:"descripcion 1" },
//     { title: "post 2", id:2, body:"descripcion 2" },
//     { title: "post 3", id:3, body:"descripcion 3" },
//     { title: "post 4", id:4}

//   ]);
</script>

<template>
  <div class="container">
    <h1>Nire lehenengo proiektua</h1>
    <ButtonCounter />
    <ButtonCounter />

    <h2>Nire favoritoa da {{ favorito }}</h2>

    <PaginatePost
      @prev="prev"
      @next="next"
      :inicio="inicio"
      :fin="fin"
      :maxLength="posts.length"
      class="mb-2"
    >
    </PaginatePost>

    <BlogPost
      v-for="post in posts.slice(1, 10)"
      :key="post.id"
      :title="post.title"
      :id="post.id"
      :body="post.body"
      @cambiarFavoritoNombre="cambiarFavorito"
    >
      <!-- nombre de la propiedad = "metodo" -->
    </BlogPost>

    <!-- <BlogPost title="post 1" id=1 body="descripicion 1" colorText="primary"/>
    <BlogPost title="post 2" id=2 body="descripicion 2" colorText="secondary"/>
    <BlogPost title="post 3" id=3 body="descripicion 3" colorText="success"/>
    <BlogPost title="post 4" id=4 body="descripicion 4" colorText="primary"/> -->
  </div>
  <!-- <h1>Hello {{ name }}</h1> -->
  <!-- <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <main>
    <TheWelcome />
  </main> -->
</template>

<style>
/* header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
} */
</style>
