<script setup>
import { onMounted, onUnmounted } from 'vue'

onMounted(() => console.log('AboutView mounted'))
onUnmounted(() => console.log('AboutView unmounted'))
</script>

<template>
  <div class="hero bg-base-200 rounded-box p-10">
    <div class="hero-content text-center">
      <div class="max-w-md">
        <h1 class="text-5xl font-bold mb-4">About S-Mart</h1>
        <p class="py-2 text-lg">
          Welcome to our modern e-commerce platform. We are dedicated to providing the highest quality items with the best user experience.
        </p>
        <div class="divider"></div>
        <div class="text-left bg-base-100 p-6 rounded-lg shadow-sm">
          <p><strong>Developer:</strong> Youssef Emad</p>
          <p><strong>Program:</strong> ITI Scholarship Track</p>
          <p><strong>Course:</strong> VueJS Multi-Page SPA Lab</p>
        </div>
      </div>
    </div>
  </div>
</template>