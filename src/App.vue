<script setup>
import { onMounted, onUnmounted } from 'vue'
import NavBar from './components/NavBar.vue'

onMounted(() => console.log('App mounted'))
onUnmounted(() => console.log('App unmounted'))
</script>

<template>
  <div class="min-h-screen flex flex-col">
    <NavBar />
    <main class="grow container mx-auto p-4 mt-6">
      <router-view />
    </main>
  </div>
</template>