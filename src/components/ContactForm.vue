<template>
  <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
    <!-- Contact Form -->
    <div class="bg-white rounded-lg shadow-md p-6 sm:p-8">
      <h2 class="text-2xl font-bold text-primary mb-6">Send Us a Message</h2>
      <form @submit.prevent="handleSubmit" role="form" aria-label="Contact form" class="space-y-6">
        <div>
          <label for="name" class="block text-sm font-semibold text-gray-700 mb-2">
            Name <span class="text-red-500" aria-hidden="true">*</span>
          </label>
          <input
            id="name"
            v-model="formData.name"
            type="text"
            required
            aria-required="true"
            class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-accent focus:border-accent transition-colors"
            :class="{ 'border-red-500': errors.name }"
            placeholder="Your full name"
          />
          <p v-if="errors.name" class="mt-1 text-sm text-red-500" role="alert">{{ errors.name }}</p>
        </div>

        <div>
          <label for="email" class="block text-sm font-semibold text-gray-700 mb-2">
            Email <span class="text-red-500" aria-hidden="true">*</span>
          </label>
          <input
            id="email"
            v-model="formData.email"
            type="email"
            required
            aria-required="true"
            class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-accent focus:border-accent transition-colors"
            :class="{ 'border-red-500': errors.email }"
            placeholder="your.email@example.com"
          />
          <p v-if="errors.email" class="mt-1 text-sm text-red-500" role="alert">
            {{ errors.email }}
          </p>
        </div>

        <div>
          <label for="message" class="block text-sm font-semibold text-gray-700 mb-2">
            Message <span class="text-red-500" aria-hidden="true">*</span>
          </label>
          <textarea
            id="message"
            v-model="formData.message"
            required
            aria-required="true"
            rows="5"
            class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-accent focus:border-accent transition-colors resize-none"
            :class="{ 'border-red-500': errors.message }"
            placeholder="Tell us about your project or inquiry..."
          ></textarea>
          <p v-if="errors.message" class="mt-1 text-sm text-red-500" role="alert">
            {{ errors.message }}
          </p>
        </div>

        <div
          v-if="submitStatus.message"
          :class="
            submitStatus.type === 'success'
              ? 'bg-green-50 border-green-200'
              : 'bg-red-50 border-red-200'
          "
          class="p-4 rounded-lg border"
          role="alert"
        >
          <p :class="submitStatus.type === 'success' ? 'text-green-800' : 'text-red-800'">
            {{ submitStatus.message }}
          </p>
        </div>

        <button
          type="submit"
          :disabled="isSubmitting"
          class="w-full px-6 py-3 bg-accent text-white font-semibold rounded-lg shadow-md hover:bg-cyan-500 hover:shadow-lg transform hover:scale-105 transition-all focus-outline disabled:opacity-50 disabled:cursor-not-allowed disabled:transform-none"
          :aria-busy="isSubmitting"
        >
          {{ isSubmitting ? 'Sending...' : 'Send Message' }}
        </button>
      </form>
    </div>

    <!-- Contact Information -->
    <div class="space-y-6">
      <div class="bg-white rounded-lg shadow-md p-6 sm:p-8">
        <h2 class="text-2xl font-bold text-primary mb-6">Get In Touch</h2>
        <div class="space-y-4">
          <div class="flex items-start space-x-4">
            <div class="flex-shrink-0">
              <svg
                class="w-6 h-6 text-accent"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
                aria-hidden="true"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"
                />
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"
                />
              </svg>
            </div>
            <div>
              <h3 class="font-semibold text-gray-900 mb-1">Address</h3>
              <p class="text-gray-600">123 TechNova Ave<br />Silicon City</p>
            </div>
          </div>

          <div class="flex items-start space-x-4">
            <div class="flex-shrink-0">
              <svg
                class="w-6 h-6 text-accent"
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
            </div>
            <div>
              <h3 class="font-semibold text-gray-900 mb-1">Email</h3>
              <a
                href="mailto:contact@technova.com"
                class="text-accent hover:text-cyan-600 transition-colors focus-outline rounded"
              >
                contact@technova.com
              </a>
            </div>
          </div>

          <div class="flex items-start space-x-4">
            <div class="flex-shrink-0">
              <svg
                class="w-6 h-6 text-accent"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
                aria-hidden="true"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"
                />
              </svg>
            </div>
            <div>
              <h3 class="font-semibold text-gray-900 mb-1">Phone</h3>
              <a
                href="tel:+15551234567"
                class="text-accent hover:text-cyan-600 transition-colors focus-outline rounded"
              >
                +1 555-123-4567
              </a>
            </div>
          </div>
        </div>
      </div>

      <!-- Map -->
      <div class="bg-white rounded-lg shadow-md overflow-hidden h-64">
        <iframe
          src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3168.639290845301!2d-122.08424938469223!3d37.42199997982574!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x808fba02425dad8f%3A0x6c296c66619367e0!2sGoogleplex!5e0!3m2!1sen!2sus!4v1234567890123!5m2!1sen!2sus"
          width="100%"
          height="100%"
          style="border: 0"
          allowfullscreen
          loading="lazy"
          referrerpolicy="no-referrer-when-downgrade"
          title="TechNova office location map"
          aria-label="Google Maps showing TechNova office location"
        ></iframe>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, reactive } from 'vue'

const formData = reactive({
  name: '',
  email: '',
  message: '',
})

const errors = reactive({
  name: '',
  email: '',
  message: '',
})

const submitStatus = reactive({
  message: '',
  type: '',
})

const isSubmitting = ref(false)

const validateForm = () => {
  let isValid = true
  errors.name = ''
  errors.email = ''
  errors.message = ''

  if (!formData.name.trim()) {
    errors.name = 'Name is required'
    isValid = false
  }

  if (!formData.email.trim()) {
    errors.email = 'Email is required'
    isValid = false
  } else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(formData.email)) {
    errors.email = 'Please enter a valid email address'
    isValid = false
  }

  if (!formData.message.trim()) {
    errors.message = 'Message is required'
    isValid = false
  }

  return isValid
}

const handleSubmit = async () => {
  if (!validateForm()) {
    return
  }

  isSubmitting.value = true
  submitStatus.message = ''

  try {
    await new Promise((resolve) => setTimeout(resolve, 1000))

    submitStatus.message = 'Thank you for your message! We will get back to you soon.'
    submitStatus.type = 'success'

    formData.name = ''
    formData.email = ''
    formData.message = ''

    setTimeout(() => {
      submitStatus.message = ''
    }, 5000)
  } catch {
    submitStatus.message = 'Something went wrong. Please try again later.'
    submitStatus.type = 'error'
  } finally {
    isSubmitting.value = false
  }
}
</script>
