<template>
  <transition name="fade">
    <div class="vue-modal form" v-show="open">
      <transition name="drop-in">
        <div class="vue-modal-inner" v-show="open">
          <div class="vue-modal-content">
            <form action="">
              <h3>Title</h3>
              <input
                @input="$emit('handle-title', $event)"
                type="text"
                name="title"
                required
              /><br />
              <h3>Description</h3>
              <input
                type="text"
                name="description"
                required
                @change="$emit('handle-description', $event)"
              /><br />
              <input
                type="file"
                name="img"
                @change="$emit('handle-img', $event)"
              />
            </form>
            <br />
            <div class="button-group">
              <button class="discard-btn" type="button" @click="$emit('close')">
                Discard
              </button>
              <button class="publish-btn" @click="$emit('handle-submit')">
                Publish
              </button>
            </div>
          </div>
        </div>
      </transition>
    </div>
  </transition>
</template>

<script>
import Button from "./Button.vue";
export default {
  components: { Button },
  name: "Modal",
  props: {
    open: {
      type: Boolean,
      default: true,
    },

    methods: {},
    emits: ["file-selected", "handle-submit"],
  },
};
</script>

<style scoped>
::before,
::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.vue-modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  overflow-x: hidden;
  overflow-y: auto;
  background-color: rgba(0, 0, 0, 0.4);
  z-index: 1;
}

.vue-modal-inner {
  max-width: 500px;
  margin: 2rem auto;
}

.vue-modal-content {
  color: white;
  position: relative;
  background-color: black;
  border: 1px solid white;
  background-clip: padding-box;
  border-radius: 0.3rem;
  padding: 1rem;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}

.drop-in-enter-active,
.drop-in-leave-active {
  transition: all 0.3s ease-out;
}

.drop-in-enter-from,
.drop-in-leave-to {
  opacity: 0;
  transform: translate(0, -50px);
}

.button-group {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.publish-btn {
  background-color: chartreuse;
  width: 100%;
  border-radius: 10px;
}

.discard-btn {
  background: transparent;
  color: red;
  border: 1px solid red;
  width: 100%;
  border-radius: 10px;
}

.exit-btn {
  border: none;
  background: transparent;
}

form {
  max-width: 420px;
  margin: 30px auto;
  text-align: center;
  padding: 40x;
  border-radius: 10px;
}
label {
  color: #aaa;
  display: inline-block;
  margin: 20px;
}

input {
  background: transparent;
  border-radius: 10px;
  display: block;
  padding: 10px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border: 1px solid #ddd;
  color: #555;
}
</style>
