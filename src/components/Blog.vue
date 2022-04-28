<template>
  <div class="card mt-3">
    <img src="{cover_image}" class="card-img-top" alt="..." />
    <div class="card-body" style="">
      <h5 class="card-title">{{ title }}</h5>
      <p class="card-text">{{ description }}</p>
      <Button @delete-post="deletePost(id)" :id="id" />
    </div>
  </div>
</template>

<script>
import Button from "./Button.vue";
export default {
  name: "Blog",
  components: {
    Button,
  },
  props: {
    author: String,
    title: String,
    description: String,
    image: String,
    id: String,
    cover_image: String,
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
.card-body {
  background-color: black;
  text-align: center;
  color: white;
}

p {
  border-bottom: 1.5px solid white;
  text-align: justify;
  display: inline-block;
  margin: 5px;
  padding: 10px;
}
</style>
