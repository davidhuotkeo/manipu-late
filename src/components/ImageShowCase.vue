<template>
    <div class="text-left text-2xl" v-for="(img, i) in imageDisplay" :key="i">
      <div v-if="img">{{ "// " + imageName(img) }}</div>
      <a v-if="img" href="#">
        <v-lazy-image
          :src="getImagePath(img)"
          class="col-span-2 mt-4 mb-8 hover:scale-110 transition-all"
        />
      </a>
      <div v-else></div>
    </div>
</template>

<script setup>
import VLazyImage from "v-lazy-image";
</script>

<script>
export default {
  data() {
    return {
      images: [
        "bday.png",
        "bending.png",
        "connected.png",
        "divide.png",
        "duo.png",
        "group.png",
        "kosha.png",
        "link.png",
        "Meant-to-be.png",
        "no-regret.png",
        "out.png",
        "relax.png",
        "rose.png",
        "scary.png",
        "screw.png",
        "stop.png",
        "track.png",
        "tri.png",
        "uno I.png",
        "uxlaw.png",
        "waffle.png",
      ],
    };
  },
  methods: {
    imageName(img) {
      return img
        .split(".")[0]
        .replace(/\b[a-z]/g, (match) => match.toUpperCase());
    },
    getImagePath(name) {
      return new URL(`../assets/${name}`, import.meta.url);
    },
  },
  computed: {
    imageDisplay() {
      let data = [];
      this.images.forEach((img) => {
        data.push(img);
        data.push("");
      });
      return data;
    },
  }
};
</script>