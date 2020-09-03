<template>
  <div>
    <div class="flex flex-wrap mt-10 justify-center">
      <div class="container flex justify-between w-4/5 md:w-11/12">
        <!-- Name intro -->
        <div class="text-txt-pri flex flex-col self-start">
          <h1 class="text-5xl md:text-6xl font-bold mt-2">
            Best quality spices from
            <br />Kerala
          </h1>
          <p class="mt-2">
            <span class="name text-xl font-bold">BHARATEXOTICS</span>
          </p>
          <!-- End -->
          <!-- Work Section-->
          <p class="text-xs mt-10 font-bold">Featured Spices</p>
          <div class="flex flex-wrap justify-between md:space-x-4">
            <div v-for="work in modifyData()" :key="work.id">
              <mywork
                :title="work.title"
                :shortdes="work.shortdes"
                :id="work.id"
                :img="work.img"
                :key="work.id"
              />
            </div>
          </div>

          <!-- End -->
          <div class="space-x-4 mt-8 mb-16 md:self-end">
            <nuxt-link
              to="work"
              class="btncol text-white focus:outline-none focus:shadow-outline px-8 py-2 shadow rounded-full"
            >View More</nuxt-link>
          </div>
        </div>
        <div class="hidden self-start w-1/3 lg:block">
          <img src="/illus.svg" alt="illustration" />
        </div>
      </div>
    </div>

    <!-- section 2 -->
    <div class="flex flex-wrap mt-6 justify-center bg-white text-black">
      <div class="container w-4/5 md:w-11/12">
        <div class="flex flex-col self-start">
          <h1
            class="text-3xl md:text-4xl font-bold my-10"
          >Get your product supercharged with happy consumers.</h1>
          <div class="flex flex-wrap mt-6 mb-12 md:justify-between justify-around">
            <div class="flex flex-col w-56 shadow-xs p-4">
              <img src="/entrepreneure.svg" alt="featImg" class="w-48 self-center" />
              <h2 class="font-bold self-center">Entrepreneur</h2>

              <ul class="text-xs list-none mt-2 self-center">
                <li>• Identify gaps in the market</li>
                <li>• Create ways to fill gaps</li>
                <li>• Build teams deliver end product</li>
                <li>• The list is endless here :P</li>
              </ul>
            </div>
            <div class="flex flex-col w-56 shadow-xs p-4">
              <img src="/product.svg" alt="featImg" class="w-48 self-center" />
              <h2 class="font-bold self-center">Product Manager</h2>

              <ul class="text-xs list-none mt-2 self-center">
                <li>• Understand the audience</li>
                <li>• Competitive research</li>
                <li>• Build feedback synthesis</li>
                <li>• Drive product roadmaps, priorities</li>
              </ul>
            </div>
            <div class="flex flex-col w-56 shadow-xs p-4">
              <img src="/visual.svg" alt="featImg" class="w-48 self-center" />
              <h2 class="font-bold self-center">Visual designer</h2>

              <ul class="text-xs list-none mt-2 self-center">
                <li>• Application of the usual UI jargon :P</li>
                <li>• Understand brand across platforms</li>
                <li>• Make products come to life</li>
              </ul>
            </div>
            <div class="flex flex-col w-56 shadow-xs p-4">
              <img src="/dataAn.svg" alt="featImg" class="w-48 self-center" />
              <h2 class="font-bold self-center">Data Analyst</h2>

              <ul class="text-xs list-none mt-2 self-center">
                <li>• Use data for informed decisions</li>
                <li>• Create A/B tests, discover patterns</li>
                <li>• Gather insights and feedback</li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- section 3 -->
    <div class="flex flex-wrap justify-center bg-white text-black">
      <div class="container mb-12 w-4/5 md:w-11/12">
        <div class="flex flex-col self-start">
          <h1
            class="text-3xl md:text-4xl font-bold mt-10"
          >Yes these are features that I can offer for your business.</h1>
          <p class="mt-2">
            Psst: I can do much more than the features listed.
            <nuxt-link to="/contact" class="underline">Let's talk</nuxt-link>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import mywork from "@/components/mywork";
import contactme from "@/components/contactme";

import { mapActions, mapState } from "vuex";
export default {
  mounted() {
    this.getWorkData();
  },
  components: {
    mywork,
    contactme,
  },
  computed: {
    ...mapState(["workData"]),
  },
  methods: {
    ...mapActions(["loadWorkData"]),
    getWorkData() {
      this.loadWorkData();
    },
    modifyData() {
      var items = this.workData;

      var result = Object.keys(items)
        .map((key) => items[key]) // turn an array of keys into array of items.
        .filter((item) => {
          return (
            item.id == "cardamom" ||
            item.id == "cashew" ||
            item.id == "blackpepper"
          );
        });
      return result;
    },
  },
};
</script>
