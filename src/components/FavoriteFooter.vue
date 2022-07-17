<template>
  <div
    class="w-full flex items-center justify-between px-3 b-light"
    style="height: 12vh"
  >
    <div class="flex items-center">
      <div>
        <h1 class="text-sm text-white tracking-wide mb-1">
          {{ songName }}
        </h1>
        <h2 class="text-xs text-lightest tracking-wide">{{ songArtist }}</h2>
      </div>
      <button @click="$emit('toggle', current)">
        <i class="fa-solid fa-heart text-base mx-4 text-green"></i>
      </button>
    </div>
    <div>
      <div class="flex items-center">
        <button
          @click="$emit('prev')"
          class="text-lg text-lightest hover:text-white"
        >
          <i class="fa-solid fa-backward"></i>
        </button>
        <button
          @click="$emit('pause')"
          class="text-3xl text-lightest hover:text-white m-5"
        >
          <i v-if="isPlaying" class="fa-solid fa-pause"></i>
          <i v-else class="fa-solid fa-circle-play"></i>
        </button>
        <button
          @click="$emit('next')"
          class="text-lg text-lightest hover:text-white"
        >
          <i class="fa-solid fa-forward"></i>
        </button>
      </div>
    </div>
    <div class="flex items-center">
      <i class="fa-solid fa-volume-high text-base text-lightest"></i>
      <div class="ml-2 rounded-full mr-2">
        <input
          type="range"
          @change="changeing"
          class="w-20 mt-2 h1 text-black"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["songName", "songArtist", "isPlaying", "current"],
  methods: {
    changeing(e) {
      this.$emit("changeing", e);
    },
  },
};
</script>

<style></style>
