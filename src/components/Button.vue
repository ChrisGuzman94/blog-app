<template>
  <button @click="onDelete(id)" class="btn">Delete Post</button>
</template>

<script>
export default {
  name: "Button",
  props: {
    id: String,
  },
  methods: {
    onDelete(id) {
      this.$emit("delete-post", id);
    },
  },
};
</script>
<style scoped>
button {
  border-radius: 5px;
  border: 1px solid red !important;
  max-width: 100%;
  display: inline-block;
  width: 100%;
  border: none;
  padding: 10px;
  font-size: 16px;
  cursor: pointer;
  text-align: center;
  background-color: transparent;
  color: darkred;
}

button:hover {
  cursor: pointer;
  background-color: lightgrey;
}
</style>
