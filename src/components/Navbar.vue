<template>
  <div class="w-56 bg-black h-full flex-none">
    <div class="p-6">
      <img src="../assets/spot-white-words.png" class="h-10" />
    </div>
    <div class="mx-2 mb-5">
      <button
        v-for="page in pages"
        :key="page.id"
        @click="setID = page.id"
        :class="`w-full text-sm font-semibold rounded px-3 py-2 flex items-center justify-start ${
          setID === page.id ? 'bg-light text-white' : 'text-lightest'
        }`"
      >
        <i :class="`${page.icon} m-2`"></i>
        <p>{{ page.name }}</p>
      </button>
    </div>
    <div class="mx-5">
      <h1 class="text-xs text-lightest tracking-widest uppercase mb-3">
        PlayList
      </h1>
      <button
        class="flex item-center justify-start opacity-75 hover:opacity-100 mb-2"
      >
        <i class="fa-solid fa-plus" style="color: white; font-size: 1.3rem"></i>
        <p class="text-sm text-white font-semibold ml-2">Create Playlist</p>
      </button>

      <button
        class="flex item-center justify-start opacity-75 hover:opacity-100"
      >
        <i
          class="fa-solid fa-heart"
          style="color: white; font-size: 1.3rem"
        ></i>

        <p class="text-sm text-white font-semibold ml-2">Favorites</p>
      </button>
      <div class="h-px w-full bg-light my-3"></div>
    </div>

    <div class="mx-5">
      <div
        class="w-full h-10 overflow-y-scroll scrollbar scrollbar-thumb-gray-900 scrollbar-track-gray-500"
      >
        <p
          v-for="(album, index) in albums"
          class="text-lightest hover:text-white text-sm py-1"
          :key="index"
        >
          {{ album.name }}
        </p>
      </div>
      <button
        class="flex items-center justify-start text-lightest text-sm hover:text-white py-2"
      >
        <i class="fa-solid fa-circle-arrow-down mr-2"></i>
        <p class="text-sm font-semibold">Install app</p>
      </button>
    </div>
    <!-- make image here if you can if not then just leave it my brain hurts -->

    <!--  -->
  </div>
</template>

<script>
export default {
  props: ["albums", "pages"],
  data() {
    return {
      setID: "home",
    };
  },
};
</script>

<style></style>
