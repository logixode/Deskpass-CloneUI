<template>
  <div class="hello">
    <div class="scrollable flex flex-wrap">
      <div class="box" v-for="(i, index) in image" :key="index">
        <img :src="i" />
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
    let scrollInterval, rerollImg;
    let scrollItem = () => {
      scrollInterval = setInterval(() => {
        scrollable.scrollBy(0, 1);
      }, 15);
    };
    scrollItem();
    scrollable.onmouseover = () => {
      clearInterval(scrollInterval);
      // clearInterval(fadingClass);
      clearInterval(rerollImg);
    };
    scrollable.onmouseleave = () => {
      scrollItem();
      reroll();
    };

    // console.log(this.boxItem.length);
    let reroll = () => {
      // fadingClass = setTimeout(() => {
      scrollable.childNodes[1].className += " fading";
      scrollable.firstElementChild.className += " fading";
      // }, 3000);
      rerollImg = setTimeout(() => {
        let lastImg1 = document.createElement("div");
        let lastImg2 = document.createElement("div");
        lastImg1.className = "box";
        lastImg2.className = "box";
        lastImg1.innerHTML = `<img src='${this.image[this.boxItem[0]]}'>`;
        lastImg2.innerHTML = `<img src='${this.image[this.boxItem[1]]}'>`;
        scrollable.appendChild(lastImg1);
        scrollable.appendChild(lastImg2);
        this.boxItem.push(this.boxItem[0]);
        this.boxItem.push(this.boxItem[1]);
        this.boxItem.shift();
        this.boxItem.shift();
        scrollable.removeChild(scrollable.childNodes[1]);
        scrollable.removeChild(scrollable.firstChild);
        reroll();
      }, 6000);
    };
    setTimeout(() => {
      reroll();
    }, 6000);
  },
};
</script>
