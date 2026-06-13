<script setup>
import { onMounted, onUnmounted } from 'vue'

onMounted(() => console.log('CarouselBanner mounted'))
onUnmounted(() => console.log('CarouselBanner unmounted'))
</script>

<template>
  <div class="carousel w-full rounded-box mb-8 shadow-xl">
    <div id="slide1" class="carousel-item relative w-full h-64 bg-primary text-primary-content flex justify-center items-center">
      <h2 class="text-4xl font-bold">Welcome to our Store</h2>
      <div class="absolute flex justify-between transform -translate-y-1/2 left-5 right-5 top-1/2">
        <a href="#slide3" class="btn btn-circle">❮</a> 
        <a href="#slide2" class="btn btn-circle">❯</a>
      </div>
    </div> 
    <div id="slide2" class="carousel-item relative w-full h-64 bg-secondary text-secondary-content flex justify-center items-center">
      <h2 class="text-4xl font-bold">Huge Summer Discounts</h2>
      <div class="absolute flex justify-between transform -translate-y-1/2 left-5 right-5 top-1/2">
        <a href="#slide1" class="btn btn-circle">❮</a> 
        <a href="#slide3" class="btn btn-circle">❯</a>
      </div>
    </div> 
    <div id="slide3" class="carousel-item relative w-full h-64 bg-accent text-accent-content flex justify-center items-center">
      <h2 class="text-4xl font-bold">New Arrivals Daily</h2>
      <div class="absolute flex justify-between transform -translate-y-1/2 left-5 right-5 top-1/2">
        <a href="#slide2" class="btn btn-circle">❮</a> 
        <a href="#slide1" class="btn btn-circle">❯</a>
      </div>
    </div>
  </div>
</template>