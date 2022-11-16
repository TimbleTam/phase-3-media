

<template>
  <div class="home">
    <div id="video-section">
      <video id="background-video" autoplay loop muted poster="https://assets.codepen.io/6093409/river.jpg">
        <source src="https://assets.codepen.io/6093409/river.mp4" type="video/mp4">

      </video>
      <div class="title">

        <h1 class="title-text" v-bind:hidden="title_hidden" v-on:click="pick_phrase()">{{ chosen_phrase }}</h1>
      </div>
    </div>

    <HelloWorld msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'



export default {
  name: 'HomeView',
  components: {
    HelloWorld
  },

  data() {
    return {
      title_phrase: ["A new perspective.", "Make it Cinema.", "Video Speaks that speaks your language."],
      chosen_phrase: "Making it real.",
      optional_title: 'a new perspective',
      title_hidden: false,
    }

  },
  methods: {
    pick_phrase: function () {
      const time_frame = 2000 / this.chosen_phrase.length;
      console.log(this.title_phrase);

      let replacement_phrase = this.chosen_phrase;
      setTimeout(() => {
        this.start_delete(replacement_phrase, time_frame);
      }, time_frame);
    },

    start_delete: function (new_phrase, time_space) {
      let blank = new_phrase.substring(0, new_phrase.length - 1);
      this.chosen_phrase = blank;
      if (this.chosen_phrase.length > 0) {
        setTimeout(() => {
          this.start_delete(blank, time_space)
        }, time_space);
      }
      else {
        this.title_hidden = true;
        setTimeout(() => {
          this.pick_new()
        }, time_space);
      }
    },

    pick_new: function () {
      var num = Math.random() * (this.title_phrase.length - 1);
      const new_phrase = this.title_phrase[num.toFixed()];
      this.chosen_phrase = new_phrase;
      this.title_hidden = false;
    },
  },
}

</script>

<style>
#video-section {
  height: 90vh;
  width: 100vw;
}

.title {
  position: absolute;
  top: 50%;
  width: 100vw;
  transform: translateY(-50%);
  text-align: left;
  mix-blend-mode: difference;

}

.title-text {
  font-variant-caps: all-petite-caps;
  font-weight: bolder;
  font-size: 10rem;
  color: white;
  opacity: 1;
  animation: 2s title-appear;
}

@keyframes title-appear {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}





#background-video {
  filter: grayscale(70%);
  width: 100%;
  height: 90%;
  object-fit: cover;
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  z-index: -1;
}

@media (max-width: 750px) {
  #background-video {
    display: none;
  }

  body {
    background: url("https://assets.codepen.io/6093409/river.jpg") no-repeat;
    background-size: cover;
  }
}
</style>
