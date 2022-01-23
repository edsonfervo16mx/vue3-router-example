<template>
  <Titulo text="Titulo de mi Blog" />
  <!--<button @click="consumirApi">Consumir API</button>-->
  <div v-for="item in arrayBlog" :key="item.id">
    <router-link :to="'/articulo/' + item.id">
      {{ item.title }}
    </router-link>
  </div>
</template>
<script>
import Titulo from "@/components/Titulo.vue";
export default {
  components: {
    Titulo,
  },
  data() {
    return {
      arrayBlog: [],
    };
  },
  methods: {
    async consumirApi() {
      try {
        const data = await fetch("https://jsonplaceholder.typicode.com/posts");
        const array = await data.json();
        console.log(array);
        this.arrayBlog = array;
      } catch (error) {
        console.log(error);
      }
    },
  },
  created() {
    this.consumirApi();
  },
};
</script>
