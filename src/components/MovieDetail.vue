<template>
<transition name="fade">
  <div class="movie-wrapper" :style="styles">
    <div class="movie-info">
      <h1>{{ movie.title}}</h1>
      <h3>Release Date: {{ movie.release_date }}</h3>
      <p>
        {{ movie.overview }}
      </p>
    </div>
  </div>
  </transition>
</template>

<script>
const BACKDROP_PATH = "http://image.tmdb.org/t/p/w1280";
export default {
  data() {
    return {
      movie: {}
    };
  },
  created: function() {
    this.fetchData();
  },
  computed: {
    styles() {
      return {
        background: `url(${BACKDROP_PATH}/${this.movie.backdrop_path})`
      };
    }
  },
  methods: {
    fetchData: async function() {
      try {
        const res = await fetch(
          `https://api.themoviedb.org/3/movie/${
            this.$route.params.id
          }?api_key=46becdf3251e17ce10c5fd25bf8352d2`
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
.movie-wrapper {
  position: relative;
  padding-top: 50vh;
  background-size: cover;
}

.movie-info {
  background: white;
  color: #222;
  padding: 2rem 10%;
}

.fade-enter-active,
.fade-leave-active {
  transition: all 0.3s ease;
}
.fade-enter,
.fade-leave-to {
  opacity: 0;
  transform: translateX(100%);
}
</style>