<template>
  <section
    class="relative bg-gradient-to-br from-primary via-slate-800 to-primary py-20 sm:py-32 overflow-hidden"
    aria-labelledby="hero-heading"
  >
    <!-- Background Pattern -->
    <div class="absolute inset-0 opacity-10" aria-hidden="true">
      <svg class="w-full h-full" xmlns="http://www.w3.org/2000/svg">
        <defs>
          <pattern id="grid" width="40" height="40" patternUnits="userSpaceOnUse">
            <path d="M 40 0 L 0 0 0 40" fill="none" stroke="currentColor" stroke-width="1" />
          </pattern>
        </defs>
        <rect width="100%" height="100%" fill="url(#grid)" />
      </svg>
    </div>

    <div class="container mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
      <div class="max-w-4xl mx-auto text-center">
        <h1
          id="hero-heading"
          class="text-4xl sm:text-5xl lg:text-6xl font-bold text-white mb-6 fade-in"
        >
          Empowering Your Business with Innovative IT Solutions
        </h1>
        <p class="text-xl sm:text-2xl text-gray-300 mb-8 fade-in" style="animation-delay: 0.2s">
          Cloud, Cybersecurity, and Software Solutions for Modern Enterprises
        </p>
        <div
          class="flex flex-col sm:flex-row gap-4 justify-center items-center fade-in"
          style="animation-delay: 0.4s"
        >
          <router-link
            to="/services"
            class="inline-block px-8 py-4 bg-accent text-white font-semibold rounded-lg shadow-lg hover:bg-cyan-500 hover:shadow-xl transform hover:scale-105 transition-all focus-outline"
            aria-label="View our services"
          >
            Our Services
          </router-link>
          <router-link
            to="/contact"
            class="inline-block px-8 py-4 bg-transparent text-white font-semibold rounded-lg border-2 border-white hover:bg-white hover:text-primary transform hover:scale-105 transition-all focus-outline"
            aria-label="Contact us"
          >
            Contact Us
          </router-link>
        </div>
      </div>
    </div>

    <!-- Decorative Elements -->
    <div
      class="absolute top-1/4 left-10 w-20 h-20 bg-accent rounded-full opacity-20 blur-xl"
      aria-hidden="true"
    ></div>
    <div
      class="absolute bottom-1/4 right-10 w-32 h-32 bg-cyan-400 rounded-full opacity-20 blur-xl"
      aria-hidden="true"
    ></div>
  </section>
</template>

<script setup lang="ts">
import { defineOptions } from 'vue'

defineOptions({
  name: 'HeroSection',
})
</script>
