<script setup>
import { computed, onMounted, onUnmounted } from 'vue'

const props = defineProps({
  product: {
    type: Object,
    required: true
  }
})

const emit = defineEmits(['buy'])

const discountedPrice = computed(() => {
  const discountAmount = props.product.price * (props.product.discount / 100);
  return props.product.price - discountAmount;
})

const isOutOfStock = computed(() => props.product.stock <= 0)

onMounted(() => console.log(`ProductDetails mounted for: ${props.product.name}`))
onUnmounted(() => console.log(`ProductDetails unmounted for: ${props.product.name}`))
</script>

<template>
  <section class="card lg:card-side bg-base-100 shadow-xl border border-base-300">
    <figure class="lg:w-1/2 p-4">
      <img :src="product.image" :alt="product.name" class="rounded-xl w-full object-cover" />
    </figure>
    
    <div class="card-body lg:w-1/2">
      <h2 class="card-title text-3xl">
        {{ product.name }}
        <div v-if="product.badge && !isOutOfStock" class="badge badge-secondary">
          {{ product.badge }}
        </div>
        <div v-if="isOutOfStock" class="badge badge-error">
          Out of Stock
        </div>
      </h2>
      
      <p class="text-gray-500">{{ product.description }}</p>

      <div class="flex gap-2 my-2">
        <span v-for="(tag, index) in product.tags" :key="index" class="badge badge-outline">
          {{ tag }}
        </span>
      </div>

      <div class="my-2">
        <span class="font-semibold mr-2">Stock left:</span>
        <span :class="{'text-error font-bold': isOutOfStock}">{{ product.stock }}</span>
      </div>

      <div class="my-4">
        <span v-if="product.discount > 0" class="text-lg text-gray-400 line-through mr-2">
          ${{ product.price.toFixed(2) }}
        </span>
        <span class="text-3xl font-bold text-success">${{ discountedPrice.toFixed(2) }}</span>
      </div>

      <div class="card-actions justify-end mt-auto">
        <button 
          @click="emit('buy', product.id)" 
          class="btn btn-primary" 
          :disabled="isOutOfStock"
        >
          {{ isOutOfStock ? 'Check Back Later' : 'Buy Now' }}
        </button>
      </div>
    </div>
  </section>
</template>