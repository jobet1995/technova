<template>
  <article
    class="bg-white rounded-lg shadow-md hover:shadow-xl transition-shadow p-6 h-full flex flex-col border border-gray-100"
  >
    <div class="flex items-center justify-center w-16 h-16 bg-accent/10 rounded-lg mb-4">
      <component :is="iconComponent" class="w-8 h-8 text-accent" aria-hidden="true" />
    </div>
    <h3 class="text-xl font-bold text-primary mb-3">{{ title }}</h3>
    <p class="text-gray-600 mb-6 flex-grow">{{ description }}</p>
    <button
      @click="handleLearnMore"
      class="inline-flex items-center text-accent font-semibold hover:text-cyan-600 transition-colors focus-outline rounded"
      :aria-label="`Learn more about ${title}`"
    >
      Learn More
      <svg
        class="w-5 h-5 ml-2"
        fill="none"
        stroke="currentColor"
        viewBox="0 0 24 24"
        aria-hidden="true"
      >
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
      </svg>
    </button>
  </article>
</template>

<script setup lang="ts">
import { computed, h } from 'vue'

const props = defineProps({
  icon: {
    type: String,
    required: true,
    validator: (value: string) => ['consulting', 'cloud', 'security', 'development', 'support'].includes(value)
  },
  title: {
    type: String,
    required: true,
  },
  description: {
    type: String,
    required: true,
  },
})

const emit = defineEmits(['learn-more'])

const iconComponent = computed(() => {
  const icons = {
    consulting: () =>
      h('svg', { fill: 'none', stroke: 'currentColor', viewBox: '0 0 24 24' }, [
        h('path', {
          'stroke-linecap': 'round',
          'stroke-linejoin': 'round',
          'stroke-width': '2',
          d: 'M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z',
        }),
      ]),
    cloud: () =>
      h('svg', { fill: 'none', stroke: 'currentColor', viewBox: '0 0 24 24' }, [
        h('path', {
          'stroke-linecap': 'round',
          'stroke-linejoin': 'round',
          'stroke-width': '2',
          d: 'M3 15a4 4 0 004 4h9a5 5 0 10-.1-9.999 5.002 5.002 0 10-9.78 2.096A4.001 4.001 0 003 15z',
        }),
      ]),
    security: () =>
      h('svg', { fill: 'none', stroke: 'currentColor', viewBox: '0 0 24 24' }, [
        h('path', {
          'stroke-linecap': 'round',
          'stroke-linejoin': 'round',
          'stroke-width': '2',
          d: 'M9 12l2 2 4-4m5.618-4.016A11.955 11.955 0 0112 2.944a11.955 11.955 0 01-8.618 3.04A12.02 12.02 0 003 9c0 5.591 3.824 10.29 9 11.622 5.176-1.332 9-6.03 9-11.622 0-1.042-.133-2.052-.382-3.016z',
        }),
      ]),
    development: () =>
      h('svg', { fill: 'none', stroke: 'currentColor', viewBox: '0 0 24 24' }, [
        h('path', {
          'stroke-linecap': 'round',
          'stroke-linejoin': 'round',
          'stroke-width': '2',
          d: 'M10 20l4-16m4 4l4 4-4 4M6 16l-4-4 4-4',
        }),
      ]),
    support: () =>
      h('svg', { fill: 'none', stroke: 'currentColor', viewBox: '0 0 24 24' }, [
        h('path', {
          'stroke-linecap': 'round',
          'stroke-linejoin': 'round',
          'stroke-width': '2',
          d: 'M18.364 5.636l-3.536 3.536m0 5.656l3.536 3.536M9.172 9.172L5.636 5.636m3.536 9.192l-3.536 3.536M21 12a9 9 0 11-18 0 9 9 0 0118 0zm-5 0a4 4 0 11-8 0 4 4 0 018 0z',
        }),
      ]),
  }
  return icons[props.icon as keyof typeof icons] || icons.consulting
})

const handleLearnMore = () => {
  emit('learn-more')
}
</script>
