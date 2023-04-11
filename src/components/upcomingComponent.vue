<script setup>
import LocationIcon from "@/icons/LocationIcon.vue";
import youtubeIcon from "@/icons/youtubeIcon.vue";
import TimerIcon from "@/icons/TimerIcon.vue";
import audience from "@/assets/piano.jpg";
// import { useRouter } from "vue-router";
import { ref, watchEffect } from "vue";

const data = ref([
    {
        date: 10,
        month: 'April',
        time: "7:00pm",
        artist: "njerae ",
        location: "Kenya, Nairobi",
        title: "Anayefaa",
        url: 'https://www.youtube.com/watch?v=BC8-x14PHXM',
        Image: "https://source.boomplaymusic.com/group10/M00/04/03/20980aa9a2d04ef9898079a94a7c972c.jpg"
    },
    {
        date: 13,
        month: 'June',
        time: "9:00pm",
        artist: " okello max ",
        location: "Kenya, Nairobi",
        title: "Aboriti",
        url: 'https://www.youtube.com/watch?v=s6HghsZ4SLA',
        Image: "https://www.kenyanvibe.com/wp-content/uploads/2022/12/okellomax_1671088732941265-819x1024.jpg"
    }
]);

const isAvailable = ref(false)
const imageBg = ref(false)
// const router = useRouter();

imageBg.value = audience;

watchEffect(() => {
    if (data.value[0].ur != '' && data.value[0] != '') {
        isAvailable.value = true
    }
});


const listen = (url) => {
    window.open(
        `${url}`
    );
}

</script>
<template>
    <div class="upcoming-container" :style="{ 'backgroundImage': `url(${imageBg})` }">
        <div class="upcoming-title">
            <h2>Upcoming Songwriter & Artist</h2>
            <span>Keep in touch with upcoming musicians, artist and song writers concerts and events</span>
        </div>
        <div class="upcoming-wrapper">
            <!-- loop  -->
            <div class="upcoming-detail"
                v-for="({ date, time, month, artist, location, title, url, Image }, index ) in data" :key="index">
                <div class="upcoming-cover-img">
                    <div class="upcoming-date">
                        <h2>{{ date }}</h2>
                        <span>{{ month }}</span>
                    </div>
                    <img :src="Image" alt="" class="upcoming-img-p">
                    <div class="upcoming-img-d">
                        <h2>{{ title }}</h2>
                        <span>{{ artist }}</span>
                    </div>
                </div>
                <div class="time-cd">
                    <div class="upcoming-location">
                        <LocationIcon class="icon-u icon-location" />
                        <span>{{ location }}</span>
                    </div>
                    <div class="upcoming-timer">
                        <TimerIcon class="icon-u icon-timer" />
                        <span>{{ time }}</span>
                    </div>
                </div>
                <div class="upcoming-btn">
                    <button class="up-btn btn-watch" @click="listen(url)" v-if="isAvailable == true">
                        <youtubeIcon class="icon icon-youtube" />
                        listen now
                    </button>
                    <button class="up-btn btn-cancel" v-else>
                        not available
                    </button>
                </div>
            </div>
            <!-- loop  -->
        </div>
    </div>
</template>
<style>
@import "@/style/upcoming.css";
</style>