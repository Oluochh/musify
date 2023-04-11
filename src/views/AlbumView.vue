<script setup>
import ArrowIcon from "@/icons/ArrowIcon.vue";
import { ref } from "vue";

const show = ref(false);


const showMore = () => {
  show.value = !show.value;
}

const data = ref([
  {
    title: "Sauti Sol",
    image: "https://upload.wikimedia.org/wikipedia/commons/thumb/b/b9/Sauti-Sol.jpg/300px-Sauti-Sol.jpg"
  },
  {
    title: "Elani",
    image: "https://netstorage-tuko.akamaized.net/images/a48a36f4403ddcca.jpg"
  },
  {
    title: "Wanavokali",
    image: "https://netstorage-tuko.akamaized.net/images/0966d31d9cc34e10.jpeg"
  },
  {
    title: "Nvirii the story teller",
    image: "https://www.musicinafrica.net/sites/default/files/styles/profile_photo/public/images/artist_profile/202009/nvirii-1.jpg"
  },
  {
    title: "Ethan muziki",
    image: "https://afrikalyrics.com/assets/thumbnail/tempted-ethan-muziki.jpg"
  },
  {
    title: " Fena gitu phy",
    image: "https://afrikalyrics.com/assets/artistes/fena-gitu.jpg"
  },
  {
    title: "Muthoni the drummer queen",
    image: "https://anyiko-pr.com/wp-content/uploads/2022/11/Muthoni-The-Drummer-Queen-1-1-768x1024.jpg"
  },
  {
    title: "Nyashinski",
    image: "https://netstorage-tuko.akamaized.net/images/0fgjhs1d7gmp1gcqd8.jpg?imwidth=720"
  },
  {
    title: "Eric wainana ",
    image: "https://cdn.standardmedia.co.ke/sdemedia/sdeimages/sunday/zankfwh1bopih5vermx61346fa716052.jpg"
  },
  {
    title: "Billy BLack",
    image: "https://theopenspacefor.files.wordpress.com/2020/12/whatsapp-image-2020-12-02-at-8.07.34-am-e1606892234853.jpeg"
  },
  {
    title: "Avril",
    image: "https://nairobiwire.com/wp-content/uploads/2021/05/avril.jpg"
  },
  {
    title: "Victoria kimani",
    image: "https://guardian.ng/wp-content/uploads/2018/05/Victoria-Kimani.-Photo-Classic-105-e1527001312129.jpg"
  },
  {
    title: "Rayvanny",
    image: "https://netstorage-tuko.akamaized.net/images/faf124db74b60fe8.jpg?imwidth=720 "
  },
  {
    title: "Zuchu",
    image: "https://netstorage-tuko.akamaized.net/images/4f8b73f31f3ee287.png?imwidth=720 "
  },
  {
    title: "Nandy",
    image: "https://netstorage-tuko.akamaized.net/images/ef96c6701ebb4eae.jpg?imwidth=720 "
  }
])

</script>
<template>
  <div class="album-container">
    <div class="alb-inner" :class="show == true ? 'show-all-albums' : 'show-less-albums'">
      <div class="alb-title">
        <span>Songwriter and artist</span>
        <h2>Popular artist & songwriter we have worked with</h2>
      </div>
      <div class="album-wrapper">
        <div class="album-info" v-for="({ title, image }, index) in data" :key="index">
          <img :src="image" :alt="title" class="album-cover">
          <div class="name-banner">
            <h3>{{ title }}</h3>
          </div>
        </div>
      </div>
    </div>
    <div class="show-more" @click="showMore" :class="show == true ? 'hide' : ''">
      <span>see more</span>
      <ArrowIcon class="icon-more" />
    </div>
    <div class="show-more" @click="showMore" :class="show == false ? 'hide' : ''">
      <ArrowIcon class="icon-more less" />
      <span>see less</span>
    </div>
  </div>
</template>
<style>
@import "@/style/album.css";
</style>

