<template>
  <div class="about">
    <Titulo text="About" />
    <h1>This is an about page</h1>
  </div>
</template>
<script>
import Titulo from "@/components/Titulo.vue";

export default {
  name: "Home",
  components: {
    Titulo,
  },
};
</script>
