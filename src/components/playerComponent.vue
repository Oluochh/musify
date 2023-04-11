<script setup>
import youtubeIcon from "@/icons/youtubeIcon.vue";
import PlayIcon from "@/icons/PlayIcon.vue";
import PauseIcon from "@/icons/PauseIcon.vue";
import NextIcon from "@/icons/NextIcon.vue";
import PreviousIcon from "@/icons/PreviousIcon.vue";
import { ref, watchEffect, computed } from "vue";

const status = ref();
const coverImg = ref();
const isPlaying = ref(false);

const playYoutube = (link) => {
    window.open(
        `${link}`
    );
}


const songs = ref([
  {
    path: "https://raw.githubusercontent.com/Oluochh/musify/main/src/assets/music/Billy-Black-Ambia.mp3",
    title: "Ambia",
    Status: "Playing",
    artist: "Billy black",
    publish: "March",
    Year: "2022",
    company: "Musify",
    about: "Ambia by Billy black is awesome, love it 💌",
    link: 'https://www.youtube.com/watch?v=_hpSjeOvAJY',
    cover:
      "https://raw.githubusercontent.com/Oluochh/musify/main/src/assets/cover/billy-black-ambia.jpeg",
  },
  {
    path: "https://raw.githubusercontent.com/Oluochh/musify/main/src/assets/music/Ethan%20Muziki-Kesho%20Kutwa.mp3",
    title: "Kesho Kutwa",
    Status: "Playing",
    artist: "Ethan Muziki",
    publish: "February",
    Year: "2021",
    company: "Musify",
    about: "Kesho Kutwa is a melody to my ears 😤 ",
    link:'https://www.youtube.com/watch?v=SCvPqMrimrA',
    cover:
      "https://raw.githubusercontent.com/Oluochh/musify/main/src/assets/cover/ethan-kesho.jpeg",
  },
  {
    path: "https://raw.githubusercontent.com/Oluochh/musify/main/src/assets/music/FenaGitu-Steam.mp3",
    title: "Steam",
    Status: "Playing",
    artist: "Fena Gitu",
    publish: "January ",
    Year: "2019",
    company: "Musify",
    about: "Vybing with her 🎹 ",
    link: 'https://www.youtube.com/watch?v=6nPbyllBbc4',
    cover:
      "https://raw.githubusercontent.com/Oluochh/musify/main/src/assets/cover/fena-steam.jpeg",
  },
  {
    path: "https://raw.githubusercontent.com/Oluochh/musify/main/src/assets/music/NVIIRI-THE-STORYTELLER-POMBE%20SIGARA.mp3",
    title: "Pombe",
    Status: "Playing",
    artist: "Nviiri the story teller",
    publish: "January ",
    Year: "2019",
    company: "Musify",
    about: "it's good 🤔 ",
    link: 'https://www.youtube.com/watch?v=u2vt37RZdC8',
    cover:
      "https://raw.githubusercontent.com/Oluochh/musify/main/src/assets/cover/nviiri-pombe.jpeg",
  },
  {
    path: "https://raw.githubusercontent.com/Oluochh/musify/main/src/assets/music/PHY-TABOO-TAABU.mp3",
    title: "Taboo",
    Status: "Playing",
    artist: "Phy",
    publish: "September",
    Year: "2016",
    company: "Musify",
    about: "😇 perfectly good",
    link: 'https://www.youtube.com/watch?v=GHLwzpaPSXg',
    cover:
      "https://raw.githubusercontent.com/Oluochh/musify/main/src/assets/cover/phy-taboo.jpeg",
  },
  {
    path: "https://raw.githubusercontent.com/Oluochh/musify/main/src/assets/music/RitwaRiaku.mp3",
    title: "Ritwa Riaku",
    Status: "Playing",
    artist: "Ritwa Riaku",
    publish: "March",
    Year: "2020",
    company: "Musify",
    about: "no comment, just play it 😠 ",
    link: 'https://www.youtube.com/watch?v=mtUbGG9Ve0w',
    cover:
      "https://raw.githubusercontent.com/Oluochh/musify/main/src/assets/cover/ritwa.jpeg",
  },
  {
    path: "https://raw.githubusercontent.com/Oluochh/musify/main/src/assets/music/Victoria-Kimani-Show.mp3",
    title: "Show",
    Status: "Playing",
    artist: "Victoria Kimani",
    publish: "December ",
    Year: "2014",
    company: "Musify",
    about: "mmmmh....✈ ",  
    link: 'https://www.youtube.com/watch?v=YTgOCss3LYA',
    cover:
      "https://raw.githubusercontent.com/Oluochh/musify/main/src/assets/cover/victoria-show.jpeg",
  },
]);

const length = ref(0);
const songIndex = ref(0);
const currentSong = ref(
  "https://raw.githubusercontent.com/Oluochh/musify/main/src/assets/music/Billy-Black-Ambia.mp3"
);

//get info of the song playing
const playingSong = computed(() => {
  return songs.value.filter((song) => song.path.includes(currentSong.value));
});

coverImg.value = playingSong.value[0].cover;
console.log(playingSong.value[0]);
let audio = new Audio(currentSong.value);

// toggle play and pause
const play = () => {
  isPlaying.value = !isPlaying.value;
  switch (isPlaying.value) {
    case false:
      audio.pause();
      break;
    case true:
      audio.play();
      break;
    default:
      break;
  }
};

const next = () => {
  audio.pause();
  currentSong.value = songs.value[songIndex.value + 1].path;
  audio = new Audio(currentSong.value);
  isPlaying.value = true;
  audio.play();
  songIndex.value++;
  console.log(songIndex.value);

  coverImg.value = playingSong.value[0].cover;
};

const prev = () => {
  audio.pause();
  currentSong.value = songs.value[songIndex.value - 1].path;
  audio = new Audio(currentSong.value);
  isPlaying.value = true;
  audio.play();
  songIndex.value -= 1;
  coverImg.value = playingSong.value[0].cover;
};

watchEffect(() => {
  switch (isPlaying.value) {
    case true:
      status.value = playingSong.value[0].Status;
      length.value = 100;
      break;
    case false:
      status.value = "paused";
      length.value = length.value;
      break;

    default:
      break;
  }
});
</script>
<template>
  <div
    class="player-container"
    :style="{ backgroundImage: `url(${coverImg})` }"
  >
    <div class="cover" :style="{ backgroundImage: `url(${coverImg})` }">
      <div
        class="cover-info"
        v-for="({ artist, title }, index) in playingSong"
        :key="index"
      >
        <h3>{{ artist }}</h3>
        <h2>{{ title }}</h2>
      </div>
    </div>
    <div
      class="audio"
      v-for="({ title, about, publish, Year, company, link }, index) in playingSong"
      :key="index"
    >
      <div class="player-section">
        <div class="audio-wrapper">
          <div class="audio-info">
            <span> Status </span>
            <h4>{{ status }}</h4>
          </div>
          <div class="audio-controller">
            <div class="previous-audio" @click="prev">
              <PreviousIcon class="icon icon-previous" />
            </div>
            <div class="play-audio" @click="play">
              <PauseIcon class="icon icon-pause" v-if="isPlaying == true" />
              <PlayIcon class="icon icon-play-c" v-else />
            </div>
            <div class="next-audio" @click="next">
              <NextIcon class="icon icon-next" />
            </div>
          </div>
          <div class="song-status">
            <p>00:00 <span>/05:30</span></p>
          </div>
        </div>
        <div class="audio-bar">
          <span :style="{ width: `${length}%` }"></span>
        </div>
      </div>
      <div class="audio-player-info">
        <div class="inner-pa">
          <div class="audio-title">
            <h3>Featured song</h3>
            <h4>{{ title }}</h4>
          </div>
          <div class="audio-detail">
            <p>{{ about }}</p>
          </div>
          <div class="more-info">
            <div class="info-m">
              <span>Published in</span>
              <h4>{{ publish }}</h4>
            </div>
            <div class="info-m">
              <span>Year</span>
              <h4>{{ Year }}</h4>
            </div>
            <div class="info-m">
              <span>By </span>
              <h4>{{ company }}</h4>
            </div>
          </div>
          <button class="play-btn play-youtube" @click="playYoutube(link)">
            <youtubeIcon class="icon icon-youtube" />
            <span> Play on youtube</span>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
<style>
@import "@/style/player.css";
</style>
