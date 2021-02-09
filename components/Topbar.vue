<template>
  <header class="fixed">
    <button class="focus:outline-none" @click="selected = ''">
      <h1
        class="font-semibold text-gray-600 text-3xl sm:text-6xl pt-2 pl-2 sm:pt-6 sm:pl-6"
      >
        {{ title }}
      </h1>
    </button>
    <div class="grid grid-cols-1 sm:grid-cols-5 gap-1 sm:gap-4 md:gap-10">
      <h2
        v-for="heading in categories"
        :key="heading"
        class="px-1 sm:px-2 xl:px-8 font-bold text-sm sm:text-xl text-gray-500"
      >
        <button class="block focus:outline-none" @click="selected = heading">
          {{ heading }}
        </button>
      </h2>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      title: 'SITE NAME',

      selected: '',

      categories: ['item 1', 'item 2', 'item 3', 'item 4', 'item-5'],
    }
  },
  watch: {
    selected() {
      this.$emit('heading', this.selected)
    },
  },
}
</script>

<style></style>
