<script>
import { mapActions, mapState } from "pinia";
import { useRadioStore } from "../stores/counter";
import AudioPlayer from "vue3-audio-player";
// import AudioVisual from 'vue-audio-visual'
import "vue3-audio-player/dist/style.css";

export default {
  components: {
    AudioPlayer,
  },
  computed: {
    ...mapState(useRadioStore, ["oneData"]),
    // ...mapState(useMusicStore, ['oneData'])
  },
  methods: {
    ...mapActions(useRadioStore, ["move"]),
    playPause() {
      document.querySelector(".audio-wire-1").style.animationPlayState ===
      "running"
        ? (document.querySelector(".audio-wire-1").style.animationPlayState =
            "paused")
        : (document.querySelector(".audio-wire-1").style.animationPlayState =
            "running");

      document.querySelector(".audio-wire-2").style.animationPlayState ===
      "running"
        ? (document.querySelector(".audio-wire-2").style.animationPlayState =
            "paused")
        : (document.querySelector(".audio-wire-2").style.animationPlayState =
            "running");

      document.querySelector(".audio-wire-3").style.animationPlayState ===
      "running"
        ? (document.querySelector(".audio-wire-3").style.animationPlayState =
            "paused")
        : (document.querySelector(".audio-wire-3").style.animationPlayState =
            "running");

      document.querySelector(".audio-wire-4").style.animationPlayState ===
      "running"
        ? (document.querySelector(".audio-wire-4").style.animationPlayState =
            "paused")
        : (document.querySelector(".audio-wire-4").style.animationPlayState =
            "running");

      document.querySelector(".audio-wire-5").style.animationPlayState ===
      "running"
        ? (document.querySelector(".audio-wire-5").style.animationPlayState =
            "paused")
        : (document.querySelector(".audio-wire-5").style.animationPlayState =
            "running");

      document.querySelector(".audio-wire-6").style.animationPlayState ===
      "running"
        ? (document.querySelector(".audio-wire-6").style.animationPlayState =
            "paused")
        : (document.querySelector(".audio-wire-6").style.animationPlayState =
            "running");

      document.querySelector(".audio-wire-7").style.animationPlayState ===
      "running"
        ? (document.querySelector(".audio-wire-7").style.animationPlayState =
            "paused")
        : (document.querySelector(".audio-wire-7").style.animationPlayState =
            "running");

      document.querySelector(".audio-wire-8").style.animationPlayState ===
      "running"
        ? (document.querySelector(".audio-wire-8").style.animationPlayState =
            "paused")
        : (document.querySelector(".audio-wire-8").style.animationPlayState =
            "running");

      document.querySelector(".audio-wire-9").style.animationPlayState ===
      "running"
        ? (document.querySelector(".audio-wire-9").style.animationPlayState =
            "paused")
        : (document.querySelector(".audio-wire-9").style.animationPlayState =
            "running");
    },
  },
};
</script>

<template>
  <div id="audio-visual" class="d-flex">
    <div class="audio-wire audio-wire-1"></div>
    <div class="audio-wire audio-wire-2"></div>
    <div class="audio-wire audio-wire-3"></div>
    <div class="audio-wire audio-wire-4"></div>
    <div class="audio-wire audio-wire-5"></div>
    <div class="audio-wire audio-wire-6"></div>
    <div class="audio-wire audio-wire-7"></div>
    <div class="audio-wire audio-wire-8"></div>
    <div class="audio-wire audio-wire-9"></div>
  </div>

  <AudioPlayer
    :option="{
      src: oneData.url,
      title: oneData.name,
      coverImage: oneData.icon,
    }"
    @click="playPause()"
    id="music"
  />
  <div class="">
    <div class="center">
      <button
        class="btn btn-primary"
        v-if="this.$route.name === 'detailMusic'"
        @click.prevent="move('music')"
      >
        <fa icon="arrow-left" />Back
      </button>
      <button
        class="btn btn-primary"
        v-if="this.$route.name === 'player'"
        @click.prevent="move('radios')"
      >
        <fa icon="arrow-left" />Back
      </button>
    </div>
  </div>
  <div v-if="this.$route.name === 'detailMusic'">
    <h1 class="display-4">Detail Music</h1>
    <div class="center">
      <div class="row center">
        <div class="mb-5">
          <div class="bg-white rounded shadow-sm py-5 px-4 detail">
            <img :src="oneData.icon" class="img-detail" />
            <h5 class="mb-0">Artist Name: {{ oneData.name }}</h5>
            <span class="small text-uppercase tags"
              >Album: {{ oneData.album }}</span
            >
            <ul class="social mb-0 list-inline mt-3">
              <li class="list-inline-item">Release Date: {{ oneData.realeaseDate }}</li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div v-if="this.$route.name === 'player'">
    <h1 class="display-4">Detail Song</h1>
    <div class="center">
      <div class="row center">
        <div class="mb-5">
          <div class="bg-white rounded shadow-sm py-5 px-4 detail">
            <img :src="oneData.icon" class="img-detail" />
            <h5 class="mb-0">Radio Name: {{ oneData.name }}</h5>
            <span class="small text-uppercase tags"
              >Tags: {{ oneData.tags }}</span
            >
            <ul class="social mb-0 list-inline mt-3">
              <li class="list-inline-item">Votes: {{ oneData.votes }} --</li>
              <li class="list-inline-item">State: {{ oneData.state }}</li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
.tags {
  color: rgb(57, 57, 57);
}
.detail {
  background: #e8cbc0;
  background: -webkit-linear-gradient(to right, #e8cbc0, #636fa4);
  background: linear-gradient(to right, #e8cbc0, #636fa4);
  color: black;
}

.img-detail {
  object-fit: cover;
  width: 200px;
  height: 200px;
  margin-left: 85px;
  margin-right: 85px;
}
.center {
  display: flex;
  justify-content: center;
}

#audio-visual {
  height: 70px;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 40px 0px;
}
#audio-visual .audio-wire {
  height: 50%;
  margin: 0px 3px;
  padding: 0px 1px;
  background-color: rgb(221, 221, 221);
  animation: animateUpDown 0.5s infinite alternate;
}
.container h1 {
  font-size: 40px;
  font-weight: bolder;
}

.container button {
  font-weight: bolder;
  margin-bottom: 0;
}

.container p {
  font-size: 12px;
  color: rgb(134, 134, 134);
}
#audio-visual .audio-wire-1 {
  animation-delay: 50ms;
}
#audio-visual .audio-wire-2 {
  animation-delay: 150ms;
}
#audio-visual .audio-wire-3 {
  animation-delay: 300ms;
}
#audio-visual .audio-wire-4 {
  animation-delay: 450ms;
}
#audio-visual .audio-wire-5 {
  animation-delay: 600ms;
}
#audio-visual .audio-wire-6 {
  animation-delay: 450ms;
}
#audio-visual .audio-wire-7 {
  animation-delay: 300ms;
}
#audio-visual .audio-wire-8 {
  animation-delay: 150ms;
}
#audio-visual .audio-wire-9 {
  animation-delay: 50ms;
}
@keyframes animateUpDown {
  to {
    height: 90%;
  }
  from {
    height: 50%;
  }
}
</style>
