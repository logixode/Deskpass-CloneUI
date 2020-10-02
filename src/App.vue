<template>
  <div id="app">
    <Navbar />
    <div class="flex h-screen">
      <AutoScrollGallery class="lg:w-1/2" />
      <div class="lg:w-1/2"></div>
    </div>
    s
  </div>
</template>

<script>
import Navbar from "./components/Navbar.vue";
import AutoScrollGallery from "./components/AutoScrollGallery.vue";

export default {
  name: "App",
  components: {
    AutoScrollGallery,
    Navbar,
  },
};
</script>
