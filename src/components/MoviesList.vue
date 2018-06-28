<template>
  <ul>
    <li v-for="movie in movies">
      <Movie :movie="movie"/>
    </li>
  </ul>
</template>

<script>
import Movie from "./Movie.vue";
export default {
  name: "MoviesList",
  data() {
    return {
      movies: []
    };
  },
  created: function() {
    this.fetchData();
  },
  methods: {
    fetchData: async function() {
      try {
        const res = await fetch(
          "https://api.themoviedb.org/3/discover/movie?sort_by=popularity.desc&api_key=46becdf3251e17ce10c5fd25bf8352d2"
        );
        const movies = await res.json();
        this.movies = movies.results;
      } catch (error) {
        console.log(error);
      }
    }
  },
  components: {
    Movie
  }
};
</script>

<style scoped>
ul {
  list-style: none;
  display: grid;
  grid-row-gap: 1rem;
  grid-template-columns: repeat(6, 1fr);
  margin: 0;
  padding: 1rem;
}
</style>