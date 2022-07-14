<template>
  <div class="bg-dark h-screen">
    <div class="flex" style="height: 88vh">
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
            <i
              class="fa-solid fa-plus"
              style="color: white; font-size: 1.3rem"
            ></i>
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

      <div class="w-full h-full relative overflow-y-scroll">
        <!-- header -->
        <div
          class="w-full sticky top-0 p-2 flex items-center justify-between py-4 px-6 bg-dark"
        >
          <div class="flex items-center">
            <button class="rounded-full bg-black w-8 h-8">
              <i class="fa-solid fa-angle-left" style="color: white"></i>
            </button>
            <button class="rounded-full bg-black w-8 h-8 ml-2">
              <i class="fa-solid fa-angle-right" style="color: white"></i>
            </button>
          </div>

          <div class="relative">
            <button
              @click="ShowDropDown = !ShowDropDown"
              class="bg-light rounded-full py-1 px-2 flex items-center"
            >
              <img src="../assets/prof.jpg" class="rounded-full h-6 w-6 mr-2" />
              <p class="text-white font-semibold text-xs mr-3">Kote</p>
              <i
                v-if="!ShowDropDown"
                class="fa-solid fa-angle-down text-white"
              ></i>
              <i v-else class="fa-solid fa-angle-up text-white"></i>
            </button>

            <div
              v-if="ShowDropDown"
              class="absolute bg-light w-full rounded mt-1"
            >
              <button
                class="py-2 text-lightest text-sm w-full hover:text-white border-b border-lightest"
              >
                Account
              </button>

              <button
                class="py-2 text-sm text-lightest w-full hover:text-white"
              >
                Log out
              </button>
            </div>
          </div>
        </div>
        <!-- cards -->
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
              v-for="(song, index) in recents"
              :key="index"
              class="p-2 w-48 flex relative"
            >
              <div
                class="absolute w-full h-full flex items-end justify-end p-8 opacity-0 hover:opacity-100"
              >
                <div
                  class="bg-green rounded-full h-10 w-10 flex items-center justify-center"
                >
                  <i class="fa-solid fa-play text-white text-2xl"></i>
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
                v-for="(song, index) in forMe"
                :key="index"
                class="p-2 w-48 flex relative"
              >
                <div
                  class="absolute w-full h-full flex items-end justify-end p-8 opacity-0 hover:opacity-100"
                >
                  <div
                    class="bg-green rounded-full h-10 w-10 flex items-center justify-center"
                  >
                    <i class="fa-solid fa-play text-white text-2xl"></i>
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
      </div>
      <!-- end of header -->

      <!-- play bar -->
    </div>
    <div
      class="w-full flex items-center justify-between px-3 b-light"
      style="height: 12vh"
    >
      <div class="flex items-center">
        <div>
          <h1 class="text-sm text-white tracking-wide mb-1">
            Song Name goes Here!
          </h1>
          <h2 class="text-xs text-lightest tracking-wide">Artist goes here!</h2>
        </div>
        <i class="fa-solid fa-heart text-base mx-4 text-green"></i>
      </div>
      <div>
        <div class="flex items-center">
          <button class="text-lg text-lightest hover:text-white">
            <i class="fa-solid fa-backward"></i>
          </button>
          <button class="text-3xl text-lightest hover:text-white m-5">
            <i class="fa-solid fa-circle-play"></i>
          </button>
          <button class="text-lg text-lightest hover:text-white">
            <i class="fa-solid fa-forward"></i>
          </button>
        </div>
      </div>
      <div class="flex items-center">
        <i class="fa-solid fa-volume-high text-base text-lightest"></i>
        <div class="w-20 ml-3 bg-lightest rounded-full h-1"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  methods: {
    getImgUrl(imagePath) {
      return require(imagePath);
    },
  },
  data() {
    return {
      recents: [
        {
          title: "staying alive",
          artist: "Bee Gees",
          image: require("../assets/images/bee.jpeg"),
          src: require("../assets/music/recent/stayingalive.mp3"),
        },
        {
          title: "Hold The Line",
          artist: "Toto",
          image: require("../assets/images/tot.jpeg"),
          src: require("../assets/music/recent/HoldTheLine.mp3"),
        },
        {
          title: "StillStanding",
          artist: "Elton John",
          image: require("../assets/images/elt.jpeg"),
          src: require("../assets/music/recent/StillStanding.mp3"),
        },

        {
          title: "BabyComeBack",
          artist: "Player",
          image: require("../assets/images/player.jpeg"),
          src: require("../assets/music/recent/BabyComeBack.mp3"),
        },
        {
          title: "What You Won't Do for Love",
          artist: "Bobby Caldwell",
          image: require("../assets/images/bobby.jpeg"),
          src: require("../assets/music/recent/WhatYouWontDoForLove.mp3"),
        },
      ],
      forMe: [
        {
          title: "Hells Bells",
          artist: "AC/DC",
          image: require("../assets/images/ac.jpeg"),
          src: require("../assets/music/forme/acdc.mp3"),
        },
        {
          title: "The Chain",
          artist: "Fleetwood",
          image: require("../assets/images/fleet.jpeg"),
          src: require("../assets/music/forme/fleet.mp3"),
        },
        {
          title: "From the Watch Tower",
          artist: "jimi hendrix",
          image: require("../assets/images/henrix.jpeg"),
          src: require("../assets/music/forme/jimi.mp3"),
        },

        {
          title: "I was Made For Loving",
          artist: "KISS",
          image: require("../assets/images/kiss.jpeg"),
          src: require("../assets/music/forme/kiss.mp3"),
        },
        {
          title: "Take Me To The Top",
          artist: "Mötley Crüe",
          image: require("../assets/images/motley.jpeg"),
          src: require("../assets/music/forme/motley.mp3"),
        },
      ],
      ShowDropDown: false,
      pages: [
        {
          id: "home",
          name: "Home",
          icon: "fa-solid fa-house",
        },
        {
          id: "search",
          name: "Search",
          icon: "fa-solid fa-magnifying-glass",
        },
        {
          id: "library",
          name: "Your Library",
          icon: "fa-solid fa-chart-simple",
        },
      ],
      setID: "home",

      albums: [
        {
          name: "Player",
        },
        {
          name: "Bobby Caldwell",
        },
        {
          name: "Queen & David Bowie",
        },
        {
          name: "Elton John",
        },
        {
          name: "Toto",
        },
        {
          name: "Bee Gees",
        },
      ],
    };
  },
  components: {},
};
</script>

<style></style>
