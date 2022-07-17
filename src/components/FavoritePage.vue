<template>
  <div class="bg-dark h-screen">
    <div class="flex" style="height: 88vh">
      <Navbar :pages="pages" :albums="albums" />
      <div class="w-full h-full relative overflow-y-scroll">
        <!-- header -->
        <Header :ShowDropDown="ShowDropDown" />
        <!-- cards -->
        <FavoriteCards :fav="fav" @play="play" @toggle="toggle" />
      </div>

      <!-- end of header -->
      <!-- play bar -->
    </div>
    <FavoriteFooter
      :songName="songName"
      :songArtist="songArtist"
      :isPlaying="isPlaying"
      @next="next"
      @pause="pause"
      @prev="prev"
      @changeing="changee"
      :current="current"
      @toggle="toggle"
    />
  </div>
</template>

<script>
import FavoriteFooter from "./FavoriteFooter.vue";
import Header from "./Header.vue";
import Navbar from "./Navbar.vue";
import FavoriteCards from "./FavoriteCards.vue";
export default {
  props: ["favorites"],
  name: "App",

  methods: {
    changee(e) {
      this.player.volume = e.currentTarget.value / 100;
    },
    getImgUrl(imagePath) {
      return require(imagePath);
    },
    play(song) {
      if (typeof song.src != undefined) {
        this.current = song;

        this.player.src = this.current.src;
        this.songName = this.current.title;
        this.songArtist = this.current.artist;
      }
      this.player.play();
      this.player.addEventListener(
        "ended",
        function () {
          this.next();
        }.bind(this)
      );
      this.isPlaying = true;
    },
    pause() {
      this.isPlaying = !this.isPlaying;
      if (!this.isPlaying) {
        this.player.pause();
      } else {
        this.player.play();
      }
    },
    next() {
      this.index++;
      if (this.index > this.fav.length - 1) {
        this.index = 0;
      }
      this.current = this.fav[this.index];
      this.play(this.current);
    },
    prev() {
      this.index--;
      if (this.index < 0) {
        this.index = this.fav.length - 1;
      }
      this.current = this.fav[this.index];
      this.play(this.current);
    },
    toggle(current) {
      this.fav = this.fav.filter((item) => {
        return current !== item;
      });
      this.player.pause();
      this.next();
    },
  },

  data() {
    return {
      current: {},
      fav: this.favorites,
      index: 0,
      isPlaying: false,
      player: new Audio(),
      songName: "staying alive",
      songArtist: "Bee Gees",
      AddingFavorites: [],
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

      albums: [
        {
          name: "Player",
        },
        {
          name: "Bobby Caldwell",
        },
        {
          name: "Mötley Crüe",
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
  components: { Navbar, Header, FavoriteCards, FavoriteFooter },
};
</script>

<style></style>
