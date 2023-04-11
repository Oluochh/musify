<script setup>
import NavComponent from "@/components/NavComponent.vue";
import Player from "@/components/playerComponent.vue";
import Upcoming from "@/components/upcomingComponent.vue";
import background from "@/assets/background.jpg";
import Contact from "@/views/ContactView.vue";
import PlayIcon from "@/icons/PlayIcon.vue";
import audience from "@/assets/piano.jpg";
import Gallery from "./GalleryView.vue";
import piano from "@/assets/piano.jpg";
import Artist from "./ArtistView.vue";
import band from "@/assets/band.jpg";
import dry from "@/assets/dry.jpg";
import Album from "./AlbumView.vue";

import { useRouter } from "vue-router";

const router = useRouter();

const license = () => {
  router.push({ name: "license" });
};

const sample = () => {
  // window.location = "https://www.youtube.com/watch?v=6Pps4Y_CnrM";
  window.open("https://www.youtube.com/watch?v=6Pps4Y_CnrM", "_blank");
};
</script>
<script>
export default {
  data() {
    return {
      images: [],
      mainImageSrc: background,
    };
  },
  methods: {},
  created() {
    let self = this;
    this.images = [
      {
        image: background,
      },
      {
        image: audience,
      },
      {
        image: band,
      },
      {
        image: piano,
      },
      {
        image: dry,
      },
    ];

    setInterval(function () {
      self.mainImageSrc =
        self.images[Math.floor(Math.random() * self.images.length)].image;
    }, 5000);
  },
};
</script>
<template>
  <div
    class="home-container"
    :style="{ backgroundImage: `url(${mainImageSrc})` }"
  >
    <div class="header">
      <NavComponent />
    </div>
    <div class="home-wrapper">
      <h1>Musify Publishing</h1>
      <h3><span> Publish or License </span> your music with us</h3>
      <p>
         We are home to the best song writers like Sauti sol
        , Elani , Wanavokali , Nvirii the story teller , Ethan muziki , Fena gitu phy
        ,Muthoni the drummer queen, Nyashinski , Eric wainana,  Billy BLack , Avril
        and Victoria kimani
      </p>
      <div class="home-btn">
        <button class="play-btn btn-intro" @click="sample">
          <PlayIcon class="icon icon-play" />
          watch sample
        </button>
        <button class="play-btn btn-tickets" @click="license">Licensing</button>
      </div>
    </div>
  </div>
  <div class="p-ca">
    <Player />
  </div>
  <div>
    <Album />
  </div>
  <div>
    <Upcoming />
  </div>
  <div>
    <!-- <Gallery /> -->
  </div>
  <div>
    <Artist />
  </div>
  <Contact />
</template>
<style>
@import "@/style/home.css";
</style>
