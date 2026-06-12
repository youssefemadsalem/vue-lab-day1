<script setup>
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
import Home from './components/Home.vue'
</script>

<template>
  <div class="min-h-screen flex flex-col">
    <Header />
    
    <main class="grow container mx-auto p-4">
      <Home />
    </main>

    <Footer />
  </div>
</template>