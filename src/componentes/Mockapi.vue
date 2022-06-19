<template>
  <section class="src-componentes-http-client">
    <div class="jumbotron">
      <h2>MockApi</h2>
      <hr />
      <hr />
      <br />

      <button class="btn btn-success my-3 mr-3" @click="getPostsAxios()">
        Post Axios
      </button>
      <button class="btn btn-danger my-3" @click="posts = []">CLEAR</button>
      <br />

      <div v-if="posts.length" class="table-responsive">
        <table class="table table-dark">
          <tr>
            <th>Nombre</th>
            <th>Email</th>
            <th>Edad</th>
          </tr>
          <tr v-for="(post, index) in posts" :key="index">
            <td>{{ post.nombre }}</td>
            <td>{{ post.email }}</td>
            <td>{{ post.edad }}</td>
          </tr>
        </table>
        <h5 class="alert alert-primary">
          Se encontraron {{ posts.length }} posts.
        </h5>
      </div>
      <h4 v-else class="alert alert-danger text-center">
        No se encontraron posts
      </h4>
    </div>
  </section>
</template>

<script>
export default {
  name: "src-componentes-http-client",
  props: [],
  mounted() {},
  data() {
    return {
      url: "https://628d182d3df57e983edbd628.mockapi.io/PostUsuario",
      posts: [],
    };
  },
  methods: {
    async getPostsAxios() {
      try {
        let { data } = await this.axios(this.url);
        this.posts = data;
      } catch (error) {
        console.error("Error Axios", error);
      }
    },
  },
  computed: {},
};
</script>

<style scoped lang="css">
.jumbotron {
  background-color: teal;
  color: white;
}

hr {
  background-color: #bbb;
}
</style>
