<template>
  <div>
    {{movie.title}}
  </div>
</template>

<script>
export default {
  name: "MoviesList",
  data() {
    return {
      movie: {}
    };
  },
  created: function() {
    this.fetchData();
  },
  methods: {
    fetchData: async function() {
      try {
        const res = await fetch(
          "https://api.themoviedb.org/3/movie/550?api_key=46becdf3251e17ce10c5fd25bf8352d2"
        );
        const movie = await res.json();
        this.movie = movie;
      } catch (error) {
        console.log(error);
      }
    }
  }
};
</script>

<style scoped>
</style>