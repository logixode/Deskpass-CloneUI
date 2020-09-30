<template>
  <div class="hello">
    <div class="scrollable flex flex-wrap">
      <div class="box" v-for="i in boxItem" :key="i.id"></div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    boxItem: [1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20]
  }),
  mounted() {
    let scrollable = document.querySelector(".scrollable");

    let scrollItem = () => {
      scrollable.scrollBy(0, 3);
    };

    let scrollInterval = setInterval(() => {
      scrollItem();
    }, 50);

    scrollable.onmouseover = () => {
      clearInterval(scrollInterval);
    };

    scrollable.onmouseleave = () => {
      scrollInterval = setInterval(() => {
        scrollItem();
      }, 50);
    };
  },
};
</script>