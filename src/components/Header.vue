<template>
  <header>
    <h1>Manage Posts</h1>
  </header>
</template>
<script>
import Button from "../components/Button.vue";
export default {
  name: "Header",
  components: {
    Button,
  },
};
</script>
<style scoped>
header {
  color: white;
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin: 10px;
  margin-bottom: 15px;
  padding: 5px;
  border-bottom: 1.5px solid white;
}
</style>
