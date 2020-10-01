<template>
  <div class="hello">
    <div class="scrollable flex flex-wrap">
      <div class="box" v-for="(i, index) in boxItem" :key="index">
        <img :src="image[boxItem[i]]" />
        <!-- <img :src="image[boxItem[i]]" /> -->
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
      "https://deskpass-marketing.imgix.net/tall-images/spaces-gallery-bos-workbar.jpg?crop=focalpoint&domain=deskpass-marketing.imgix.net&fit=crop&fm=pjpg&fp-x=0.5&fp-y=0.5&h=1066&ixlib=php-3.3.0&q=61&w=800 800w",
      "https://deskpass-marketing.imgix.net/tall-images/spaces-gallery-mia-building-co.jpg?crop=focalpoint&domain=deskpass-marketing.imgix.net&fit=crop&fm=pjpg&fp-x=0.5&fp-y=0.5&h=1066&ixlib=php-3.3.0&q=61&w=800 800w",
      "https://deskpass-marketing.imgix.net/tall-images/spaces-gallery-dc-metro-office.jpg?crop=focalpoint&domain=deskpass-marketing.imgix.net&fit=crop&fm=pjpg&fp-x=0.5&fp-y=0.5&h=1066&ixlib=php-3.3.0&q=61&w=800 800w",
      "https://deskpass-marketing.imgix.net/tall-images/spaces-gallery-chi-exchange-312.jpg?crop=focalpoint&domain=deskpass-marketing.imgix.net&fit=crop&fm=pjpg&fp-x=0.5&fp-y=0.5&h=1066&ixlib=php-3.3.0&q=61&w=800 800w",
    ],
    boxItem: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9],
  }),
  mounted() {
    let scrollable = document.querySelector(".scrollable");
    let scrollInterval;

    let scrollItem = () => {
      scrollInterval = setInterval(() => {
        scrollable.scrollBy(0, 1);
      }, 15);
    };
    scrollItem();

    scrollable.onmouseover = () => {
      clearInterval(scrollInterval);
    };

    scrollable.onmouseleave = () => {
      scrollItem();
    };
    // console.log(this.boxItem.length);
    let reroll = () => {
      setTimeout(() => {
        this.boxItem.push(this.boxItem[0]);
        this.boxItem.shift();
        reroll();
      }, 7000);
    };
    reroll();
  },
};
</script>
