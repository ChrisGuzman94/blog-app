<template>
  <div class="col-md-4">
    <div class="card mt-2">
      <button @click="$emit('open')">
        <fa icon="plus" class="plus" style="height: 50px" />
      </button>
      <h3>Create Post</h3>
    </div>
  </div>
</template>
<script>
export default {
  name: "CreateBlog",
  methods: {
    create() {},
  },
};
</script>

<style scoped>
.card {
  margin-top: 10px;
  justify-content: center;
  text-align: center;
  border: 3px dashed black;
  padding: 10px;
  height: 100%;
}

.plus {
  height: 50;
}

.plus:hover {
  cursor: pointer;
}

button {
  background: transparent;
  border: none;
}
</style>
