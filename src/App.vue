<template>
  <div
    class="
      grid grid-cols-3
      m-3
      gap-4
      text-dark
      md:m-20 md:grid-cols-5
      lg:grid-cols-9
    "
  >
    <nav-bar class="mb-10 col-span-3 md:col-span-5 lg:col-span-9"></nav-bar>
    <div
      class="
        main
        font-bold
        col-span-3
        mb-3
        md:mb-20 md:col-span-5
        lg:col-span-9
      "
    >
      <div id="web-title" class="mb-20">
        <div class="flex" v-for="title in titles" :key="title">
          <p class="title-text opacity-0" v-for="(word, i) in title" :key="i">
            {{ word }}
          </p>
        </div>
      </div>
    </div>
    <p class="support col-span-3 md:col-span-5 lg:col-span-9 text-left">
      SUPPORT MY ARTWORK
    </p>
    <p class="col-span-3 text-3xl opacity-60 md:col-span-5 lg:col-span-9 text-left">
      BY BUYING IT FROM ME, IT KEEPS MY MOTIVATION TO RELEASE
      THE ABSTRACT ART THAT IS DWELLING IN MY MIND
    </p>
    <div class="button-wrap col-span-3 md:col-span-5 lg:col-span-9 flex">
        <a class="mb-20 mt-8 p-6 border rounded hover:opacity-60 transition-all" href="https://t.me/KimKosei">MY TELEGRAM</a>
    </div>

    <p
      class="
        text-3xl
        col-span-3
        md:col-span-5
        lg:col-span-9
        mb-12
        text-left
        font-bold
      "
    >
      THE ARTWORKS
    </p>
    <image-show-case class="mb-20"></image-show-case>
  </div>
</template>

<script>
import ImageShowCase from "./components/ImageShowCase.vue";
import NavBar from "./components/NavBar.vue";
import Scrollbar from "smooth-scrollbar";

export default {
  data() {
    return {
      titles: ["ABSTRACT", "ART", "EXPRESSES", "EMOTIONS"],
    };
  },
  mounted() {
    const overscrollOptions = {
      enable: true,
      effect: navigator.userAgent.match(/Android/) ? "glow" : "bounce",
      damping: 0.0005,
      maxOverscroll: navigator.userAgent.match(/Android/) ? 150 : 100,
      glowColor: "#E5E5E5",
    };

    Scrollbar.init(
      document.querySelector("#app", {
        damping: overscrollOptions.damping,
        thumbMinSize: 20,
        plugins: {
          overscroll: { ...overscrollOptions },
        },
      })
    );

    const words = document.querySelectorAll(".title-text");

    let i = 0;
    words.forEach((word) => {
      word.style.animationDelay = `${i}ms`;
      i += 75;
    });
  },
  components: { NavBar, ImageShowCase },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Fira+Sans+Condensed:wght@400;700&display=swap");

html {
  background-color: #f3f3f3;
}

#app {
  font-family: "Fira Sans Condensed", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  max-width: 100vw;
  max-height: 100vh;
  overflow: auto;
}

.main {
  font-size: calc((100vw - 1rem) / 5.5);
  line-height: calc((100vw - 1rem) / 7.5);
}

.support {
    font-size: calc((100vw - 1rem) / 8);
    line-height: calc((100vw - 1rem) / 8.5);
}

@keyframes goShowing {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

.title-text {
  animation: goShowing 500ms forwards;
}
</style>
