<template>
  <article
    class="bg-white rounded-lg shadow-md p-6 text-center hover:shadow-xl transition-shadow group"
  >
    <div class="relative w-32 h-32 mx-auto mb-4">
      <div
        class="w-full h-full rounded-full bg-gradient-to-br from-accent to-cyan-600 flex items-center justify-center text-white text-4xl font-bold group-hover:scale-110 transition-transform"
      >
        {{ initials }}
      </div>
    </div>
    <h3 class="text-xl font-bold text-primary mb-1">{{ name }}</h3>
    <p class="text-accent font-semibold mb-3">{{ position }}</p>
    <p class="text-gray-600 text-sm mb-4">{{ bio }}</p>
    <div class="flex justify-center space-x-3" role="list" :aria-label="`${name}'s social links`">
      <a
        v-if="linkedin"
        :href="linkedin"
        target="_blank"
        rel="noopener noreferrer"
        class="text-gray-400 hover:text-accent transition-colors focus-outline rounded p-1"
        :aria-label="`${name}'s LinkedIn profile`"
      >
        <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
          <path
            d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"
          />
        </svg>
      </a>
      <a
        v-if="twitter"
        :href="twitter"
        target="_blank"
        rel="noopener noreferrer"
        class="text-gray-400 hover:text-accent transition-colors focus-outline rounded p-1"
        :aria-label="`${name}'s Twitter profile`"
      >
        <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
          <path
            d="M23 3a10.9 10.9 0 01-3.14 1.53 4.48 4.48 0 00-7.86 3v1A10.66 10.66 0 013 4s-4 9 5 13a11.64 11.64 0 01-7 2c9 5 20 0 20-11.5a4.5 4.5 0 00-.08-.83A7.72 7.72 0 0023 3z"
          />
        </svg>
      </a>
      <a
        v-if="email"
        :href="`mailto:${email}`"
        class="text-gray-400 hover:text-accent transition-colors focus-outline rounded p-1"
        :aria-label="`Email ${name}`"
      >
        <svg
          class="w-5 h-5"
          fill="none"
          stroke="currentColor"
          viewBox="0 0 24 24"
          aria-hidden="true"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"
          />
        </svg>
      </a>
    </div>
  </article>
</template>

<script setup lang="ts">
import { computed } from 'vue'

const props = defineProps({
  name: {
    type: String,
    required: true,
  },
  position: {
    type: String,
    required: true,
  },
  bio: {
    type: String,
    required: true,
  },
  linkedin: {
    type: String,
    default: '',
  },
  twitter: {
    type: String,
    default: '',
  },
  email: {
    type: String,
    default: '',
  },
})

const initials = computed(() => {
  return props.name
    .split(' ')
    .map((word) => word.charAt(0))
    .join('')
    .toUpperCase()
    .slice(0, 2)
})
</script>
