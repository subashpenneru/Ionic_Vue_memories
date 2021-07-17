<template>
  <base-layout :pageTitle="loadedMemory.title" page-default-back="/memories">
    <p v-if="!loadedMemory">Could not find a memory for the selected</p>
    <template v-else>
      <memory-overview
        :title="loadedMemory.title"
        :image="loadedMemory.image"
        :description="loadedMemory.description"
      ></memory-overview>
    </template>
  </base-layout>
</template>

<script>
import MemoryOverview from '../components/memories/MemoryOverview.vue';

export default {
  components: {
    MemoryOverview,
  },
  data() {
    return {
      memoryId: this.$route.params.id,
    };
  },
  computed: {
    loadedMemory() {
      return this.$store.getters.getMemory(this.memoryId);
    },
  },
};
</script>
