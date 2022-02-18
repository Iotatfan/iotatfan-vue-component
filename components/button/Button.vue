<template>
  <button
    type="button"
    class="io-btn"
    :class="[buttonClass, ...customClass]"
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
        default: () => {
              return ""
          }
      },
      customClass: {
        type: Array,
        default: () => {
            return []
        }
      },
      disabled: {
        type: Boolean,
        default: () => {
          return false
        }
      }
  },
  computed: {
    buttonClass: function() {
      switch(this.buttonType) {
        case 'discord':
          return 'io-btn-discord'
        case 'transparent':
          return 'io-btn-transparent'
        case 'no-border':
          return 'io-btn-no-border'
        default:
          return 'io-btn'
      }
    }
  },
  methods: {
    handleClick() {
      this.$emit('click')
    },
  }
};
</script>

<style scoped>
.btn-label  {
  font-style: normal;
  font-weight: bold;
  font-size: 1.5rem;
  vertical-align: middle;
}
</style>