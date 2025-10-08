<template>
  <header class="sticky top-0 z-40 bg-primary shadow-lg">
    <nav
      role="navigation"
      aria-label="Main navigation"
      class="container mx-auto px-4 sm:px-6 lg:px-8"
    >
      <div class="flex items-center justify-between h-16">
        <router-link
          to="/"
          class="flex items-center space-x-2 focus-outline rounded"
          aria-label="TechNova Home"
        >
          <svg
            class="w-8 h-8 text-accent"
            fill="currentColor"
            viewBox="0 0 24 24"
            aria-hidden="true"
          >
            <path d="M13 10V3L4 14h7v7l9-11h-7z" />
          </svg>
          <span class="text-x1 font-bold text-white">TechNova</span>
        </router-link>

        <!--Desktop Navigation-->
        <div class="hidden md:flex items-center space-x-1">
          <router-link
            v-for="link in navLinks"
            :key="link.path"
            :to="link.path"
            class="px-4 py-2 text-gray-300 hover:text-white hover:bg-primary/80 rounded transition-colors focus-outline"
            :class="{ 'text-accent border-b-2 border-accent': isActive(link.path) }"
            :aria-current="isActive(link.path) ? 'page' : null"
          >
            {{ link.name }}
          </router-link>
        </div>

        <!--Mobile Menu Button-->
        <button
          @click="toggleMenu"
          class="md:hidden p-2 rounded text-gray-300 hover:text-white hover:bg-primary/80 focus-outline"
          :aria-expanded="isMenuOpen"
          aria-controls="mobile-menu"
          aria-label="Toggle Navigation Menu"
        >
          <svg
            v-if="!isMenuOpen"
            class="w-6 h-6"
            fill="none"
            stroke="currentColor"
            viewBox="0 0 24 24"
            aria-hidden="true"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M4 6h16M4 12h16M4 18h16"
            />
          </svg>
          <svg
            v-else
            class="w-6 h-6"
            fill="none"
            stroke="currentColor"
            viewBox="0 0 24 24"
            aria-hidden="true"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M6 18L18 6M6 6l12 12"
            />
          </svg>
        </button>
      </div>

      <!--Mobile Menu Overlay-->
      <transition name="fade">
        <div
          v-if="isMenuOpen"
          @click="toggleMenu"
          class="fixed inset-0 bg-black bg-opacity-50 md:hidden"
          aria-hidden="true"
        ></div>
      </transition>

      <!--Mobile Menu-->
      <transition name="slide">
        <div
          v-if="isMenuOpen"
          id="mobile-menu"
          role="menu"
          class="fixed top-16 right-0 bottom-0 w-64 bg-primary shadow-xl md:hidden slide-in"
        >
          <div class="flex flex-col p-4 space-y-2">
            <router-link
              v-for="link in navLinks"
              :key="link.path"
              :to="link.path"
              @click="toggleMenu"
              role="menuitem"
              class="px-4 py-3 text-gray-300 hover:text-white hover:bg-primary/80 rounded transition-colors focus-outline"
              :class="{ 'text-accent bg-primary/60': isActive(link.path) }"
              :aria-current="isActive(link.path) ? 'page' : null"
            >
              {{ link.name }}
            </router-link>
          </div>
        </div>
      </transition>
    </nav>
  </header>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()
const isMenuOpen = ref(false)

const navLinks = [
  { name: 'Home', path: '/' },
  { name: 'About', path: '/about' },
  { name: 'Services', path: '/services' },
  { name: 'Projects', path: '/projects' },
  { name: 'Team', path: '/team' },
  { name: 'Contact', path: '/contact' },
]

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const isActive = (path: string) => {
  return route.path === path
}
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.slide-enter-active,
.slide-leave-active {
  transition: transform 0.3s ease-out;
}

.slide-enter-from,
.slide-leave-out {
  transform: translateX(100%);
}
</style>
