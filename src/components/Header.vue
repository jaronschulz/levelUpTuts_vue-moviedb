<template>
  <header>
    <h1><router-link to="/"> {{title }}</router-link></h1>
  </header>
</template>

<script>
export default {
  name: "Header",
  props: {
    title: String
  },
  data() {
    return {
      show: false
    };
  }
};
</script>

<style scoped>
header {
  background-color: #111;
  color: white;
  padding: 20px;
}
h1 {
  margin: 0;
}
</style>