<template>
  <div class="modal">
    <div class="modal-content">
      <slot />
      <button @click="handleClose">Close</button>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "modal-vue",
  methods: {
    handleClose() {
      this.$emit("closeModal");
    },
  },
});
</script>

<style lang="scss" scoped>
.modal {
  position: fixed;
  aspect-ratio: 3/4;
  bottom: 0;
  right: 0;
  left: 0;
  z-index: 10;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
  transition: bottom 1s;

  .modal-content {
    background: #fff;
    width: 100%;
    height: 100%;
    padding: 20px;
  }
}
</style>
