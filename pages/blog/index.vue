<template>
  <div class="container mt-5">
    <div class="card my-2" v-for="(item, index) in articulos" :key="index">
      <div class="card-body">
        <h1>
          <nuxt-link :to="`/blog/${item.id}`">{{item.title}}</nuxt-link>
        </h1>
        <p>{{item.body}}</p>
      </div>
    </div>
  </div>
</template>
<script >
import axios from "axios";
export default {
  data() {
    return {
      articulos: []
    };
  },
  async created() {
    try {
      const res = await axios.get(
        "https://jsonplaceholder.typicode.com/posts?_limit=10"
      );
      this.articulos = res.data;
      console.log(res.data);
    } catch (error) {
      console.log(error);
    }
  }
};
</script>
