<template>
  <div
    class="flex h-screen bg-fixed bg-center bg-cover background-image-custom"
  >
    <Topbar @heading="showFunction" />

    <ProjectGrid
      v-if="showProject"
      :heading="selectedHeading"
      @openModal="openModal"
    />
    <ProjectModal v-if="showProjectModal">
      <template #button>
        <button class="flex justify-end" @click="showProjectModal = false">
          <span class="font-bold"> X </span>
        </button>
      </template>
    </ProjectModal>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showProject: false,
      selectedHeading: '',
      showProjectModal: false,
    }
  },
  methods: {
    showFunction(item) {
      this.selectedHeading = item

      item.length > 0 ? (this.showProject = true) : (this.showProject = false)
    },
    openModal(open) {
      this.showProjectModal = open
    },
  },
}
</script>

<style>
.background-image-custom {
  background-image: url('https://source.unsplash.com/random/800x600');
}
</style>
