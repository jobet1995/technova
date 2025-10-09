<template>
  <section
    class="relative bg-gradient-to-br from-primary via-slate-800 to-primary overflow-hidden"
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
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center py-20 sm:py-32">
        <!-- Text Content -->
        <div class="text-center lg:text-left">
          <h1
            id="hero-heading"
            class="text-4xl sm:text-5xl lg:text-6xl font-bold text-white mb-6 hero-slide-left"
          >
            Empowering Your Business with Innovative IT Solutions
          </h1>
          <p
            class="text-xl sm:text-2xl text-gray-300 mb-8 hero-slide-left"
            style="animation-delay: 0.2s"
          >
            Cloud, Cybersecurity, and Software Solutions for Modern Enterprises
          </p>
          <div
            class="flex flex-col sm:flex-row gap-4 justify-center lg:justify-start items-center hero-slide-left"
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

        <!-- Image Grid -->
        <div class="relative hero-slide-right">
          <div class="grid grid-cols-2 gap-4">
            <div class="space-y-4">
              <div class="hero-float" style="animation-delay: 0.1s">
                <img
                  src="https://images.pexels.com/photos/3184465/pexels-photo-3184465.jpeg?auto=compress&cs=tinysrgb&w=600"
                  alt="Team collaborating on technology project"
                  class="w-full h-48 sm:h-64 object-cover rounded-lg shadow-2xl"
                  loading="lazy"
                />
              </div>
              <div class="hero-float" style="animation-delay: 0.3s">
                <img
                  src="https://images.pexels.com/photos/3182773/pexels-photo-3182773.jpeg?auto=compress&cs=tinysrgb&w=600"
                  alt="Modern office workspace with computers"
                  class="w-full h-32 sm:h-40 object-cover rounded-lg shadow-2xl"
                  loading="lazy"
                />
              </div>
            </div>
            <div class="space-y-4 mt-8">
              <div class="hero-float" style="animation-delay: 0.2s">
                <img
                  src="https://images.pexels.com/photos/3183197/pexels-photo-3183197.jpeg?auto=compress&cs=tinysrgb&w=600"
                  alt="Professional analyzing data on screen"
                  class="w-full h-32 sm:h-40 object-cover rounded-lg shadow-2xl"
                  loading="lazy"
                />
              </div>
              <div class="hero-float" style="animation-delay: 0.4s">
                <img
                  src="https://images.pexels.com/photos/3184292/pexels-photo-3184292.jpeg?auto=compress&cs=tinysrgb&w=600"
                  alt="Server room with modern technology"
                  class="w-full h-48 sm:h-64 object-cover rounded-lg shadow-2xl"
                  loading="lazy"
                />
              </div>
            </div>
          </div>

          <!-- Decorative Animated Elements -->
          <div
            class="absolute -top-4 -right-4 w-24 h-24 bg-accent rounded-full opacity-20 blur-2xl hero-pulse"
            aria-hidden="true"
          ></div>
          <div
            class="absolute -bottom-4 -left-4 w-32 h-32 bg-cyan-400 rounded-full opacity-20 blur-2xl hero-pulse"
            style="animation-delay: 1s"
            aria-hidden="true"
          ></div>
        </div>
      </div>
    </div>

    <!-- Background Animated Elements -->
    <div
      class="absolute top-1/4 left-10 w-20 h-20 bg-accent rounded-full opacity-20 blur-xl hero-pulse"
      aria-hidden="true"
    ></div>
    <div
      class="absolute bottom-1/4 right-10 w-32 h-32 bg-cyan-400 rounded-full opacity-20 blur-xl hero-pulse"
      style="animation-delay: 0.5s"
      aria-hidden="true"
    ></div>
    <div
      class="absolute top-1/2 left-1/4 w-16 h-16 bg-cyan-300 rounded-full opacity-10 blur-xl hero-pulse"
      style="animation-delay: 1.5s"
      aria-hidden="true"
    ></div>
  </section>
</template>

<script setup lang="ts">
import { defineOptions } from 'vue'

defineOptions({
  name: 'MainHero',
})
</script>

<style scoped>
@keyframes slideLeft {
  from {
    opacity: 0;
    transform: translateX(-50px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes slideRight {
  from {
    opacity: 0;
    transform: translateX(50px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes float {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-10px);
  }
}

@keyframes pulse {
  0%,
  100% {
    opacity: 0.2;
    transform: scale(1);
  }
  50% {
    opacity: 0.3;
    transform: scale(1.1);
  }
}

.hero-slide-left {
  animation: slideLeft 0.8s ease-out forwards;
  opacity: 0;
}

.hero-slide-right {
  animation: slideRight 0.8s ease-out forwards;
  opacity: 0;
  animation-delay: 0.2s;
}

.hero-float {
  animation: float 3s ease-in-out infinite;
}

.hero-pulse {
  animation: pulse 3s ease-in-out infinite;
}
</style>
