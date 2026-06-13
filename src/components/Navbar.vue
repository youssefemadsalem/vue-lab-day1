<script setup>
import { onMounted, onUnmounted } from 'vue'

defineProps({
  totalStock: {
    type: Number,
    required: true
  }
})

onMounted(() => console.log('NavBar mounted'))
onUnmounted(() => console.log('NavBar unmounted'))
</script>

<template>
  <nav class="navbar bg-base-300 shadow-md">
    <div class="flex-1">
      <RouterLink to="/" class="btn btn-ghost text-xl">S-Mart</RouterLink>
    </div>
    <div class="flex-none gap-4">
      <div class="badge badge-primary">Total Stock: {{ totalStock }}</div>
      
      <ul class="menu menu-horizontal px-1">
        <li><RouterLink to="/">Home</RouterLink></li>
        <li><RouterLink to="/about">About</RouterLink></li>
      </ul>
    </div>
  </nav>
</template>