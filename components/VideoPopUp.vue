<template>
  <div v-if="videoUrl" id="popup" class="islands__popup show-popup">
    <div>
      <div
        id="popup-close"
        class="islands__popup-close"
        @click="closePopUp"
      >
        <i class="bx bx-x"></i>
      </div>
      <iframe
        class="islands__popup-video"
        :src="videoUrl"
        title="YouTube"
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen
      ></iframe>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    videoUrl: {
      type: String,
      required: true
    }
  },
  methods: {
    closePopUp() {
      this.$emit('close')
    }
  }
}
</script>

<style scoped>
.islands__popup {
  /* display: none; */
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  background-color: var(--first-color-lighter);
  padding: 1rem 0.75rem;
  border-radius: 1rem;
  z-index: 300;
}
.islands__popup-close {
  position: absolute;
  top: -0.75rem;
  right: -0.75rem;
  display: inline-flex;
  padding: 0.35rem;
  background-color: var(--first-color);
  color: var(--first-color-lighter);
  font-size: 1.2rem;
  border-radius: 50%;
  cursor: pointer;
}
.show-popup {
  display: block;
}
</style>