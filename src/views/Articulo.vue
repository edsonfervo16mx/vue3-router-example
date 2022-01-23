<template>
  <Titulo text="Articulos" />
  <h2>{{ $route.params.id }}</h2>
  <h3>
    {{ articulo.title }}
  </h3>
  <p>
    {{ articulo.body }}
  </p>
</template>
<script>
import Titulo from "@/components/Titulo.vue";

export default {
  name: "Home",
  components: {
    Titulo,
  },
  data() {
    return {
      articulo: {},
    };
  },
  methods: {
    async getPost() {
      try {
        const data = await fetch(
          `https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`
        );
        const array = await data.json();
        console.log(array);
        this.articulo = array;
      } catch (error) {
        console.log(error);
      }
    },
  },
  created() {
    this.getPost();
  },
};
</script>
