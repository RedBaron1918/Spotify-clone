<template>
  <router-view @addFavorites="addFavorites" :favorites="favorites" />
</template>

<script>
export default {
  data() {
    return {
      favorites: [],
    };
  },
  methods: {
    addFavorites(e) {
      this.favorites = e;
    },
  },
};
</script>

<style></style>
