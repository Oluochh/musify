<script setup>
import QuoteIcon from '../icons/QuoteIcon.vue';
import { ref } from 'vue';

const show = ref(false);


const data = ref([
  {
    title: "Ali kiba",
    image: "https://upload.wikimedia.org/wikipedia/commons/thumb/3/3a/Ali_Kiba_2017.jpg/530px-Ali_Kiba_2017.jpg"
  },
  {
    title: "Diamond",
    image: "https://upload.wikimedia.org/wikipedia/commons/thumb/5/51/Diamond_Platnumz_2.png/402px-Diamond_Platnumz_2.png"
  },
  {
    title: "Ray C",
    image: "https://upload.wikimedia.org/wikipedia/commons/a/a1/Ray_C_performing_2008.jpg"
  },
  {
    title: "Sauti Sol",
    image: "https://upload.wikimedia.org/wikipedia/commons/thumb/b/b9/Sauti-Sol.jpg/300px-Sauti-Sol.jpg"
  },
  {
    title: "Elani",
    image: "https://netstorage-tuko.akamaized.net/images/a48a36f4403ddcca.jpg"
  },
  {
    title: "Harmonize",
    image: "https://upload.wikimedia.org/wikipedia/commons/thumb/9/96/Harmonize.jpg/220px-Harmonize.jpg"
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
const showMore = () => {
  show.value = !show.value;
}

</script>
<template>
  <div class="artist-container">
    <div class="artist-title">
      <span>Artists</span>
      <p>Musify publishing group works with artist
        from East Africa on securing copyright protection, licensing the use of the managed
        artist's music in various media, and collecting royales on behalf of the copyright
        owners. We constantly try to evolve and update our roster so as to reach as many artist.
        A full update of the current roster is under review and will be updated as soon as
        possible.</p>
    </div>
    <div class="gallery-layout" :class="show == true ? 'show-all-gallery' : 'show-less-gallery'">
      <div v-for="({ title, image }, index) in data" :key="index">
        <img :src="image" class="img-responsive" :alt="title">
        <span>{{ title }}</span>
      </div>
    </div>
    <div class="show-more" @click="showMore" :class="show == true ? 'hide' : ''">
      <span>See more gallery</span>
    </div>
    <div class="show-more" @click="showMore" :class="show == false ? 'hide' : ''">
      <span>Hide gallery</span>
    </div>
    <div class="inspiration-q">
      <QuoteIcon class="icon-quote" />
      <h3>Music is the universal language of mankind</h3>
      <span> ― Henry Wadsworth Longfellow</span>
    </div>
  </div>
</template>
<style>
@import "@/style/artist.css";
</style>
