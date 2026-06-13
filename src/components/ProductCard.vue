<script setup>
import { computed, onMounted, onUnmounted } from 'vue'

const props = defineProps({
  product: {
    type: Object,
    required: true
  }
})

const finalPrice = computed(() => {
  const discountAmount = props.product.price * (props.product.discount / 100);
  return props.product.price - discountAmount;
})

onMounted(() => console.log(`ProductCard mounted for: ${props.product.name}`))
onUnmounted(() => console.log(`ProductCard unmounted for: ${props.product.name}`))
</script>

<template>
  <div class="card bg-base-100 shadow-md border border-base-200">
    <figure class="px-4 pt-4 relative">
      <img :src="product.image" :alt="product.name" class="rounded-xl w-full object-cover h-48" />
      <div v-if="product.badge" class="absolute top-6 right-6 badge badge-secondary shadow-sm">
        {{ product.badge }}
      </div>
    </figure>
    <div class="card-body items-center text-center">
      <h4 class="card-title text-lg">{{ product.name }}</h4>
      
      <div>
        <span v-if="product.discount > 0" class="text-sm text-gray-400 line-through mr-2">
          ${{ product.price.toFixed(2) }}
        </span>
        <span class="font-bold text-lg">${{ finalPrice.toFixed(2) }}</span>
      </div>
      
      <div class="card-actions mt-4 w-full">
        <RouterLink :to="`/product/${product.id}`" class="btn btn-outline btn-primary w-full">
          View Product
        </RouterLink>
      </div>
    </div>
  </div>
</template>