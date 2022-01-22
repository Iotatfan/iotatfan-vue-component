<template>
  <button
    type="button"
    class="io-btn"
    :class="[buttonClass]"
    :disabled="disabled"
    @click="handleClick"
  >
  <span class="btn-label">
    {{ label }}
  </span>
  </button>
</template>

<script>
export default {
  name: "IoButton",
  props: {
      label: {
          type: String,
          default: () => {
              return ""
          }
      },
      buttonType: {
        type: String,
        required: true,
        default: () => {
              return ""
          }
      }
      // btnIndex: {
      //     type: Number,
      //     default: () => {
      //         return 0
      //     }
      // }
  },
  methods: {
    handleClick() {
      this.$emit('click')
    }
  }
};
</script>

<style scoped>
.btn-label  {
  font-style: normal;
  font-weight: bold;
  font-size: 1rem;
  vertical-align: middle;
}
</style>