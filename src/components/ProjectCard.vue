<template>
  <article
    class="bg-white rounded-lg shadow-md overflow-hidden group hover:shadow-xl transition-shadow"
  >
    <div class="relative overflow-hidden h-48 bg-gradient-to-br from-primary to-accent">
      <div
        class="absolute inset-0 flex items-center justify-center text-white text-6xl font-bold opacity-20"
      >
        {{ title.charAt(0) }}
      </div>
      <div
        class="absolute inset-0 bg-primary/60 opacity-0 group-hover:opacity-100 transition-opacity flex items-center justify-center"
      >
        <div class="text-center px-4">
          <p class="text-white font-semibold mb-4">View Details</p>
          <button
            @click="handleViewDetails"
            class="inline-block px-6 py-2 bg-accent text-white rounded-lg hover:bg-cyan-500 transform hover:scale-105 transition-all focus-outline"
            :aria-label="`View details for ${title}`"
          >
            Learn More
          </button>
        </div>
      </div>
    </div>
    <div class="p-6">
      <h3 class="text-xl font-bold text-primary mb-2">{{ title }}</h3>
      <div class="flex flex-wrap gap-2 mb-3">
        <span
          v-for="tech in techStack"
          :key="tech"
          class="px-3 py-1 bg-accent/10 text-accent text-sm rounded-full"
        >
          {{ tech }}
        </span>
      </div>
      <p class="text-gray-600 text-sm">{{ description }}</p>
    </div>
  </article>
</template>

<script setup lang="ts">
import type { PropType } from 'vue'
const props = defineProps({
  title: {
    type: String,
    required: true,
  },
  techStack: {
    type: Array as PropType<string[]>,
    required: true,
  },
  description: {
    type: String,
    required: true,
  },
  id: {
    type: [String, Number],
    required: true,
  },
})

const emit = defineEmits(['view-details'])

const handleViewDetails = () => {
  emit('view-details', props.id)
}
</script>
