<template>
  <div class="flex flex-col min-h-screen">
    <Navbar />
    <main class="flex-grow">
      <router-view />
    </main>
    <Footer />
  </div>
</template>

<script setup lang="ts">
import Navbar from './Navbar.vue'
import Footer from './Footer.vue'
defineOptions({
  name: 'AppLayout',
})
</script>
