<template>
  <Home @addFavorites="addFavorites" />
</template>

<script>
// @ is an alias to /src
import Home from "../components/Home.vue";

export default {
  name: "HomeView",
  components: {
    Home,
  },
  methods: {
    addFavorites(e) {
      this.$emit("addFavorites", e);
    },
  },
};
</script>
