<template>
  <div id="app">
    <Navbar />
    <div class="grid grid-cols-12 lg:h-screen">
      <AutoScrollGallery
        class="lg:col-span-6 col-span-12 absolute lg:relative -z-10 lg:z-0"
      />
      <div class="lg:col-span-6 col-span-12 lg:px-6 ">
        <div
          class="lg:my-24 lg:pr-24 card-sm card-sm-full mx-auto v-center lg:text-left text-center"
        >
          <h1
            class="lg:text-6xl sm:text-5xl text-4xl font-semibold leading-tight"
          >
            Workspaces<br />you'll <span class="line-b-blue">love</span>.
          </h1>
          <p class="lg:text-2xl text-xl lg:my-10 my-8">
            Instant access to 500+ nationwide coworking spaces for one monthly
            price.
          </p>

          <h4 class="text-lg">Sign up for your free 30-day trial!</h4>
          <div class="lg:flex lg:my-4 my-2 lg:-ml-6">
            <div
              class="lg:border-2 sm:block lg:rounded-full lg:border-gray-400 lg:px-6 lg:py-3 lg:mr-2"
            >
              <input
                type="text"
                placeholder="Email Address"
                class="my-2 lg:my-0 lg:border-r-2 sm-full form-sm lg:px-0 lg:py-0 border-gray-400 lg:pr-8"
              />
              <input
                type="number"
                placeholder="Zip"
                class="my-2 lg:my-0 lg:w-20 lg:ml-4 sm-full form-sm border-gray-400"
              />
            </div>
            <button class="my-2 lg:my-0 sm-full">
              Find Spaces Near Me
            </button>
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
