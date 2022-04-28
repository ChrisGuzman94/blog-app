<template>
  <div class="col-md-4" :key="blog._id" v-for="blog in blogs">
    <Blog
      :author="blog.author"
      :description="blog.description"
      :title="blog.title"
      :id="blog._id"
      :cover-image="blog.cover_image"
      @delete-post="deletePost(blog._id)"
    />
  </div>
</template>
<script>
import Blog from "./Blog.vue";
export default {
  name: "BlogsList",
  components: {
    Blog,
  },
  props: {
    blogs: Array,
  },
  methods: {
    deletePost(id) {
      this.$emit("delete-post", id);
    },
  },
  emits: ["delete-post"],
};
</script>
<style>
.col {
  display: table-cell;
  padding: 10px;
}
</style>
