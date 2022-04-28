<template>
  <div class="container">
    <Header />

    <div class="row">
      <Modal
        :open="isOpen"
        @close="isOpen = !isOpen"
        @handle-title="handleInput"
        @handle-description="handleInput"
        @handle-img="handleInput"
        @handle-submit="handleSubmit"
      />

      <CreateBlog @open="isOpen = !isOpen" />

      <BlogsList @delete-post="deletePost" :blogs="blogs" />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Header from "./components/Header.vue";
import BlogsList from "./components/BlogsList.vue";
import CreateBlog from "./components/CreateBlog.vue";
import Modal from "./components/Modal.vue";
import { ref } from "vue";

export default {
  name: "App",
  components: {
    Header,
    BlogsList,
    CreateBlog,
    Modal,
  },
  mounted() {
    let res = axios
      .get("http://localhost:8000/api/posts/")
      .then((res) => (this.blogs = res.data))
      .then((res) => console.log(res));
  },

  setup() {
    const isOpen = ref(false);

    return { isOpen };
  },
  data() {
    return {
      blogs: [],
      formValues: {
        author: "Author",
        title: "",
        description: "",
        cover_image: null,
      },
    };
  },

  methods: {
    deletePost(id) {
      this.blogs = this.blogs.filter((blog) => blog.id != id);
      axios
        .delete(`http://localhost:8000/api/posts/${id}`)
        .then((res) => console.log(res));
    },
    handleInput(event) {
      const name = event.target.name;
      const value = event.target.value;
      switch (name) {
        case "title":
          this.formValues.title = value;
          break;

        case "description":
          this.formValues.description = value;

        case "img":
          this.formValues.cover_image = event.target.files[0];

          break;

        default:
      }
    },
    handleSubmit() {
      const fd = new FormData();
      fd.append("author", this.formValues.author);
      fd.append("title", this.formValues.title);
      fd.append("description", this.formValues.description);
      fd.append(
        "cover_image",
        this.formValues.cover_image,
        this.formValues.cover_image.name
      );

      console.log(fd);

      axios
        .post("http://localhost:8000/api/posts/", fd)
        .then((res) => console.log(res))
        .catch((error) => console.log(error));
    },
  },
  created() {
    this.blogs = [];
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: "Poppins", sans-serif;
  background: #141414 !important;
  color: #ffffff;
}
.container {
  max-width: 960px;
  margin-right: auto;
  margin-left: auto;
  padding-right: 15px;
  padding-left: 15px;
  min-height: 100vh;
}

.row {
  display: table;
}

.row {
  display: flex;
  flex-wrap: wrap;
  margin: 0px 8x;
}
</style>
