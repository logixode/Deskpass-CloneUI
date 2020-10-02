<template>
  <div id="app">
    <Navbar />
    <div class="flex h-screen">
      <AutoScrollGallery class="lg:w-1/2" />
      <div class="lg:w-1/2 px-6">
        <div class="my-24 pr-24">
          <h1 class="text-6xl font-semibold leading-tight">
            Workspaces<br />you'll
            <span class="border-b-8 border-blue-600">love</span>.
          </h1>
          <p class="text-2xl my-10">
            Instant access to 500+ nationwide coworking spaces for one monthly
            price.
          </p>

          <h4 class="text-lg">Sign up for your free 40-day trial!</h4>
          <div class="flex my-4 -ml-6">
            <div class="border-2 rounded-full border-gray-400 px-6 py-3 mr-2">
              <input
                type="text"
                placeholder="Email Address"
                class="border-r-2 border-gray-400 pr-8"
              />
              <input type="number" placeholder="Zip" class="w-20 ml-4" />
            </div>
            <button>Find Spaces Near Me</button>
          </div>
          <p>
            Need space for your team?
            <a href="#" class="blue">Learn More <sub>></sub></a>
          </p>
        </div>
      </div>
    </div>
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
