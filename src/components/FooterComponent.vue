<script setup>
import logo from "@/assets/logo.png";
import { RouterLink } from 'vue-router';
import wave from "@/assets/Soundwave.png";
import { useRouteStore } from '@/stores/route';

import { ref } from "vue";

const footImg = ref();
const routeStore = useRouteStore();

footImg.value = wave;
</script>
<template>
  <div class="footer-container" :style="{ 'backgroundImage': `url(${footImg})` }">
    <img :src="logo" alt="logo" class="logo">
    <div class="footer-wrapper">
        <RouterLink :to="{ name: 'home' }" class="nav-link">Home</RouterLink>
        <RouterLink :to="{ name: 'about' }" class="nav-link">About</RouterLink>
        <RouterLink :to="{ name: 'album' }" class="nav-link">SongWriter</RouterLink>
        <RouterLink :to="{ name: 'gallery' }" class="nav-link">gallery</RouterLink>
        <RouterLink :to="{ name: 'artist' }" class="nav-link">Artists</RouterLink>
        <RouterLink :to="{ name: 'license' }" class="nav-link">License</RouterLink>
        <RouterLink :to="{ name: 'contact' }" class="nav-link">Contact</RouterLink>
    </div>
    <div class="footer-info">
      <h3>&#169;2023 Musify .All right reserved</h3>
    </div>
  </div>
</template>
<style>
@import "@/style/footer.css";
</style>
