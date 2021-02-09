// eslint-disable

<template>
  <div class="flex">
    <div class="bg-transparent w-screen flex justify-center overflow-y-scroll">
      <div id="main" class="pt-40 w-2/3 ml-6">
        <div
          v-for="(n, index) in elements"
          :key="n"
          class="h-96 fading-text mb-6"
          :class="n"
        >
          <button
            class="bg-pink-300 w-full h-full"
            @click="$emit('openModal', true)"
          >
            {{ heading }} project {{ index }} - click me to see modal!
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    heading: {
      type: String,
      default: '',
    },
  },
  data() {
    return {
      elements: [
        'element-1',
        'element-2',
        'element-3',
        'element-4',
        'element-5',
      ],

      observer: '',
    }
  },
  watch: {
    heading() {
      const element = document.getElementById('main')
      element.scrollIntoView({
        behavior: 'smooth',
        block: 'start',
        inline: 'nearest',
      })
    },
  },
  mounted() {
    this.observer = new IntersectionObserver(this.handleScroll, {
      threshold: [0.9],
    })
    this.elements.forEach((element) => {
      this.observer.observe(document.querySelector(`.${element}`))
    })
  },
  methods: {
    handleScroll(entries) {
      // The callback will return an array of entries, even if you are only observing a single item
      entries.map((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add('visible')
          // console.log('visible')
        } else {
          entry.target.classList.remove('visible')
        }
        return 0
      })
    },
  },
}
</script>

<style>
.fading-text {
  opacity: 0;
  transition: opacity 1s ease;
}
.fading-text.visible {
  opacity: 1;
}
</style>
