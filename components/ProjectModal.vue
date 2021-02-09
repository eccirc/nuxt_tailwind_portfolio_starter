<template>
  <div class="fixed overflow-auto w-screen h-screen gray-overlay flex">
    <div
      class="relative p-8 rounded-md bg-white w-11/12 h-11/12 m-auto flex-col flex"
    >
      <slot name="button"></slot>

      <div class="flex overflow-x-scroll">
        <div id="1" class="flex-none w-full h-96 bg-gray-400 mr-1">image 1</div>
        <div id="2" class="flex-none w-full h-96 bg-gray-400 mr-1">image 2</div>
        <div id="3" class="flex-none w-full h-96 bg-gray-400 mr-1">image 3</div>
      </div>
      <div class="flex w-full justify-center">
        <button @click="scrollTo('1')">
          <div class="w-auto h-full bg-gray-500 p-1 mx-1">image 1</div>
        </button>
        <button @click="scrollTo('2')">
          <div class="w-auto h-full bg-gray-500 p-1 mx-1">image 2</div>
        </button>
        <button @click="scrollTo('3')">
          <div class="w-auto h-full bg-gray-500 p-1 mx-1">image 3</div>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      open: false,
    }
  },
  methods: {
    scrollTo(id) {
      const element = document.getElementById(id)
      element.scrollIntoView({
        behavior: 'smooth',
        block: 'start',
        inline: 'nearest',
      })
    },
  },
}
</script>

<style>
.gray-overlay {
  background-color: rgba(191, 165, 165, 0.45);
}
</style>
