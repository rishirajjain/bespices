<template>
  <div class="space-y-4 flex flex-col justify-center items-center">
    <div class="container flex flex-col w-4/5 md:w-11/12 mb-8">
      <div class="self-start font-bold text-3xl text-txt-pri">Tracoph - Blog</div>
      <div class="mt-3 name font-bold">Travel, Code, Photography, Design, Entrepreneurship</div>
      <div class="flex flex-col">
        <p class="text-sm font-semibold mt-8 text-txt-pri">Latest Posts</p>
        <myblogs
          v-for="blog in blogData"
          :key="blog.id"
          :title="blog.title"
          :description="blog.description"
          :blogid="blog.id"
          :img="blog.img"
          :hashtags="blog.tags"
          :publishDate="blog.datePub"
        />
      </div>
    </div>
  </div>
</template>

<script>
import myblogs from "@/components/myblogs";
import { mapState, mapActions } from "vuex";

export default {
  mounted() {
    this.getBlogData();
  },
  computed: {
    ...mapState(["blogData"]),
  },
  components: {
    myblogs,
  },
  methods: {
    ...mapActions(["loadBlogData"]),
    getBlogData() {
      this.loadBlogData();
    },
  },
  head() {
    return {
      title: "Blog",
      meta: [
        {
          hid: "description",
          name: "description",
          content:
            "Blog on design, photography, travel, art, entrepreneurship, coding.",
        },
      ],
    };
  },
};
</script>
