<template>
  <div class="px-6 py-3">
    <div class="flex items-center justify-between">
      <h1
        class="text-2xl pl-2 font-semibold text-white tracking-wider hover:underline"
      >
        Recently Played
      </h1>
      <h2
        class="text-xs pr-6 pt-4 mb-3 text-lightest uppercase tracking-wider hover:underline"
      >
        See All
      </h2>
    </div>

    <div class="w-full flex flex-wrap">
      <div
        v-for="song in recents"
        :key="song.src"
        class="p-2 w-48 flex relative"
      >
        <div
          class="absolute w-full h-full flex items-end justify-end p-8 opacity-0 hover:opacity-100"
        >
          <div
            class="bg-green rounded-full h-10 w-10 flex items-center justify-center"
          >
            <button @click="$emit('play', song)">
              <i class="fa-solid fa-play text-white text-2xl"></i>
            </button>
          </div>
        </div>
        <div class="bg-light w-full h-auto p-5 rounded-lg shadow-md">
          <img
            :src="song.image"
            alt=""
            class="h-auto w-full shadow mb-2 rounded-full"
          />
          <h2 class="text-sm font-semibold text-white tracking-wide">
            {{ song.title }}
          </h2>
          <h3 class="text-xs text-lightest tracking-wide">
            {{ song.artist }}
          </h3>
        </div>
      </div>
    </div>
    <div class="px-1 py-3">
      <div>
        <h1
          class="text-2xl pl-2 font-semibold text-white tracking-wider hover:underline"
        >
          For me
        </h1>
      </div>

      <div class="w-full flex flex-wrap">
        <div
          v-for="song in forMe"
          :key="song.src"
          class="p-2 w-48 flex relative"
        >
          <div
            class="absolute w-full h-full flex items-end justify-end p-8 opacity-0 hover:opacity-100"
          >
            <div
              class="bg-green rounded-full h-10 w-10 flex items-center justify-center"
            >
              <button @click="$emit('play', song)">
                <i class="fa-solid fa-play text-white text-2xl"></i>
              </button>
            </div>
          </div>
          <div class="bg-light w-full h-auto p-5 rounded-lg shadow-md">
            <img
              :src="song.image"
              alt=""
              class="h-auto w-full shadow mb-2 rounded-full"
            />
            <h2 class="text-sm font-semibold text-white tracking-wide">
              {{ song.title }}
            </h2>
            <h3 class="text-xs text-lightest tracking-wide">
              {{ song.artist }}
            </h3>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["recents", "forMe"],
};
</script>

<style></style>
