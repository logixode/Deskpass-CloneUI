<template>
  <div class="hello">
    <div
      class="scrollable h-screen lg:p-3 p-1 flex flex-wrap"
      @scroll="scrollingComponent"
    >
      <div class="image-left block">
        <div class="box" v-for="(i, index) in imgLeft" :key="index">
          <!-- {{ index % 2 ? "s" : "b" }} -->
          <!-- <img class="image-left" :src="i" v-if="i % 2" /> -->
          <!-- <img class="image-right" :src="i" v-else /> -->
          <img :src="i" />
          <!-- <img :src="image[boxItem[i]]" /> -->
        </div>
      </div>
      <div class="image-right block">
        <div class="box" v-for="(i, index) in imgRight" :key="index">
          <!-- {{ index % 2 ? "s" : "b" }} -->
          <!-- <img class="image-left" :src="i" v-if="i % 2" /> -->
          <!-- <img class="image-right" :src="i" v-else /> -->
          <img :src="i" />
          <!-- <img :src="image[boxItem[i]]" /> -->
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    image: [
      "https://deskpass-marketing.imgix.net/tall-images/spaces-gallery-den-novel.jpg?crop=focalpoint&amp;domain=deskpass-marketing.imgix.net&amp;fit=crop&amp;fm=pjpg&amp;fp-x=0.5&amp;fp-y=0.5&amp;h=1066&amp;ixlib=php-3.3.0&amp;q=61&amp;w=800 800w",
      "https://deskpass-marketing.imgix.net/tall-images/spaces-gallery-bos-workbar.jpg?crop=focalpoint&domain=deskpass-marketing.imgix.net&fit=crop&fm=pjpg&fp-x=0.5&fp-y=0.5&h=1066&ixlib=php-3.3.0&q=61&w=800 800w",
      "https://deskpass-marketing.imgix.net/tall-images/spaces-gallery-atl-alkaloid-networks.jpg?crop=focalpoint&domain=deskpass-marketing.imgix.net&fit=crop&fm=pjpg&fp-x=0.5&fp-y=0.5&h=1066&ixlib=php-3.3.0&q=61&w=800 800w",
      "https://deskpass-marketing.imgix.net/tall-images/spaces-gallery-hou-ranch.jpg?crop=focalpoint&domain=deskpass-marketing.imgix.net&fit=crop&fm=pjpg&fp-x=0.5&fp-y=0.5&h=1066&ixlib=php-3.3.0&q=61&w=800 800w",
      "https://deskpass-marketing.imgix.net/tall-images/spaces-gallery-atx-impact-hub.jpg?crop=focalpoint&domain=deskpass-marketing.imgix.net&fit=crop&fm=pjpg&fp-x=0.5&fp-y=0.5&h=1066&ixlib=php-3.3.0&q=61&w=800 800w",
      "https://deskpass-marketing.imgix.net/tall-images/spaces-gallery-la-cross-campus.jpg?crop=focalpoint&domain=deskpass-marketing.imgix.net&fit=crop&fm=pjpg&fp-x=0.5&fp-y=0.5&h=1066&ixlib=php-3.3.0&q=61&w=800 800w",
      "https://deskpass-marketing.imgix.net/tall-images/spaces-gallery-mia-building-co.jpg?crop=focalpoint&domain=deskpass-marketing.imgix.net&fit=crop&fm=pjpg&fp-x=0.5&fp-y=0.5&h=1066&ixlib=php-3.3.0&q=61&w=800 800w",
      "https://deskpass-marketing.imgix.net/tall-images/spaces-gallery-dc-metro-office.jpg?crop=focalpoint&domain=deskpass-marketing.imgix.net&fit=crop&fm=pjpg&fp-x=0.5&fp-y=0.5&h=1066&ixlib=php-3.3.0&q=61&w=800 800w",
      "https://deskpass-marketing.imgix.net/tall-images/spaces-gallery-chi-exchange-312.jpg?crop=focalpoint&domain=deskpass-marketing.imgix.net&fit=crop&fm=pjpg&fp-x=0.5&fp-y=0.5&h=1066&ixlib=php-3.3.0&q=61&w=800 800w",
      "https://deskpass-marketing.imgix.net/tall-images/spaces-gallery-bos-workbar.jpg?crop=focalpoint&domain=deskpass-marketing.imgix.net&fit=crop&fm=pjpg&fp-x=0.5&fp-y=0.5&h=1066&ixlib=php-3.3.0&q=61&w=800 800w",
    ],
    imgLeft: [],
    imgRight: [],
    boxItemLeft: [0, 1, 2, 3, 4],
    boxItemRight: [0, 1, 2, 3, 4],
    rerolled: false,
  }),
  created() {
    this.imgLeft = this.image.splice(0, this.image.length / 2);
    this.imgRight = this.image;
  },
  mounted() {
    let scrollable = document.querySelector(".scrollable");
    let scrollInterval;
    let scrollItem = () => {
      scrollInterval = setInterval(() => {
        scrollable.scrollTop += 1;
      }, 10);
    };
    scrollItem();

    scrollable.onmouseover = () => {
      clearInterval(scrollInterval);
    };
    scrollable.onmouseleave = () => {
      scrollItem();
    };
  },
  methods: {
    scrollingComponent() {
      let scroll = document.querySelector(".scrollable").scrollTop;
      if (scroll > 600 && !this.rerolled) {
        console.log("reroll");
        this.rerollImg();
        this.rerolled = true;
      }
      if (scroll < 600 && this.rerolled) {
        console.log("angka turun");
        this.rerolled = false;
      }
      if (scroll > 750) {
        console.log("mepet bos");
        this.rerolled = false;
      }
      // console.log(document.querySelector(".scrollable").scrollTop);
    },
    rerollImg() {
      let imgLeft = document.querySelector(".image-left");
      let imgRight = document.querySelector(".image-right");

      let lastImgLeft = document.createElement("div");
      let lastImgRight = document.createElement("div");

      lastImgLeft.className = "box";
      lastImgRight.className = "box";

      lastImgLeft.innerHTML = `<img src='${
        this.imgLeft[this.boxItemLeft[0]]
      }'>`;
      lastImgRight.innerHTML = `<img src='${
        this.imgRight[this.boxItemRight[0]]
      }'>`;

      imgLeft.appendChild(lastImgLeft);
      imgRight.appendChild(lastImgRight);

      this.boxItemLeft.push(this.boxItemLeft[0]);
      this.boxItemRight.push(this.boxItemRight[0]);

      this.boxItemLeft.shift();
      this.boxItemRight.shift();

      imgLeft.removeChild(imgLeft.firstChild);
      imgRight.removeChild(imgRight.firstChild);
    },
  },
};
</script>
