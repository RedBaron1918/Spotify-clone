<template>
  <div class="bg-dark h-screen">
    <div class="flex" style="height: 88vh">
      <Navbar :pages="pages" :albums="albums" />
      <div class="w-full h-full relative overflow-y-scroll">
        <!-- header -->
        <Header :ShowDropDown="ShowDropDown" />
        <!-- cards -->
        <Cards :recents="recents" :forMe="forMe" @play="play" />
      </div>

      <!-- end of header -->
      <!-- play bar -->
    </div>
    <Footer
      :songName="songName"
      :songArtist="songArtist"
      :isPlaying="isPlaying"
      @next="next"
      @pause="pause"
      @prev="prev"
      @changeing="changee"
    />
  </div>
</template>

<script>
import Footer from "./Footer.vue";
import Header from "./Header.vue";
import Navbar from "./Navbar.vue";
import Cards from "./Cards.vue";
export default {
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
      if (this.index > this.recents.length - 1) {
        this.index = 0;
      }
      this.current = this.recents[this.index];
      this.play(this.current);
    },
    prev() {
      this.index--;
      if (this.index < 0) {
        this.index = this.recents.length - 1;
      }
      this.current = this.recents[this.index];
      this.play(this.current);
    },
  },
  data() {
    return {
      current: {},
      index: 0,
      isPlaying: false,
      player: new Audio(),
      songName: "staying alive",
      songArtist: "Bee Gees",
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
  components: { Navbar, Header, Cards, Footer },
  created() {
    this.current = this.recents[this.index];
    this.player.src = this.current.src;
    //this.player.play();
  },
};
</script>

<style></style>
