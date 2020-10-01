<template>
  <div id="app">
    <Navbar />
    <div class="flex h-screen">
      <AutoScrollGallery class="w-1/2" />
      <div class="w-1/2">
        <div class="grid grid-rows-3 grid-flow-col gap-4">
          <div class="row-start-3 row-span-2  bg-green-500">s</div>
          <div class="row-start-2 row-span-4  bg-green-500">a</div>
          <div class="row-end-2 row-span-4  bg-green-500">2</div>
        </div>
        <div class="grid grid-rows-3 grid-flow-col gap-4">
          <div class="row-start-2 row-span-2  bg-green-500">s</div>
          <div class="row-end-3 row-span-2  bg-green-500">a</div>
        </div>
      </div>
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
