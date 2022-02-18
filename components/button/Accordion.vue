<template>
  <div class="accordion">
    <button 
      class="accordion-header io-btn" 
      @click="toggleAccordion"
    >
      <div class="flex flex-row">
        <fa-icon 
          class="header-icon"
          :class="[ isOpen ? 'rotate' : '']"
          :icon="['fas', 'chevron-right']" 
        />
        <slot name="title"/>
      </div>
    </button>
    <transition
      name="accordion"
      @before-enter="beforeEnter"
      @enter="enter"
      @before-leave="beforeLeave"
      @leave="leave"
    >
      <div 
        class="accordion-collapse" 
        v-show="isOpen"
      >
        <div class="accordion-body">
          <slot name="body"/>
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isOpen: false
    }
  },
  methods: {
    toggleAccordion: function() {
      this.isOpen = !this.isOpen
    },
    beforeEnter: function(el) {
      el.style.height = 0
    },
    enter: function(el) {
      el.style.height = `${el.scrollHeight}px`;
    },
    beforeLeave: function(el) {
      el.style.height = `${el.offsetHeight}px`;
    },
    leave: function(el) {
      el.style.height = 0
    },
  },
}
</script>

<style scoped>

.accordion-header .flex-row {
  align-items: center;
}

.accordion {
  padding: .5rem 1rem 1rem 1rem;
}

.accordion-header {
  background: var(--dark-grey);
  color: white;
  width: 100%;
  margin-bottom: -.1rem;
  border-radius: .25rem;
  font-style: normal;
  font-weight: bold;
  font-size: 1.5rem;
  vertical-align: middle;
  text-align: left;
}

.accordion-body {
  color: white;
  width: 100%;
  text-align: left;
}

.accordion-collapse {
  background: var(--semi-dark-grey);
  transition: height 300ms linear;
  border-radius: 0 0 .25rem.25rem;
  overflow: hidden;
}

.header-icon {
  transform: rotate(0deg);
  transition-duration: 350ms;
}

.header-icon.rotate {
  transform: rotate(90deg);
  transition-duration: 350ms;
}

</style>>