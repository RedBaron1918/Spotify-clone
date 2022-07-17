<template>
  <FavoritePage :favorites="favorites" />
</template>

<script>
import FavoritePage from "../components/FavoritePage.vue";

export default {
  components: { FavoritePage },
  props: ["favorites"],
  created() {
    console.log(this.favorites);
  },
};
</script>
