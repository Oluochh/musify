<script setup>
import ArrowIcon from "@/icons/ArrowIcon.vue";
import { ref } from "vue";

const show = ref(false);


const showMore = () => {
  show.value = !show.value;
}

</script>
<template>
  <div class="gallery-container">
    <div class="gl-inner" :class="show == true ? 'show-all-gallerys' : 'show-less-gallerys'">
      <div class="gl-title">
        <span>Video gallery</span>
        <h2>Performance in action</h2>
      </div>
      <div class="gallery-wrapper">
        <div class="gallery-info">
          <video class="gallery-cover" controls>
            <source src="https://www.youtube.com/watch?v=6Pps4Y_CnrM"
              type="video/mp4" />
          </video>
          <span>Genre</span>
          <h3>Song title</h3>
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
@import "@/style/gallery.css";
</style>

