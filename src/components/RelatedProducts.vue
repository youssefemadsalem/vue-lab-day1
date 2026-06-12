<script setup>
import { computed } from 'vue'

// Define the prop this component expects to receive from the parent
const props = defineProps({
  products: {
    type: Array,
    required: true
  }
})

// Calculate percentage discounts for the array items based on the prop
const productsWithPrices = computed(() => {
  return props.products.map(item => {
    const discountAmount = item.price * (item.discount / 100);
    return {
      ...item,
      finalPrice: item.price - discountAmount
    }
  })
})
</script>

<template>
  <section>
    <h3 class="text-2xl font-bold mb-4">Related Products</h3>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
      
      <div v-for="item in productsWithPrices" :key="item.id" class="card bg-base-100 shadow-sm border border-base-200">
        <figure class="px-4 pt-4">
          <img :src="item.image" :alt="item.name" class="rounded-xl" />
        </figure>
        <div class="card-body items-center text-center">
          <h4 class="card-title text-lg">{{ item.name }}</h4>
          
          <div>
            <span v-if="item.discount > 0" class="text-sm text-gray-400 line-through mr-2">
              ${{ item.price.toFixed(2) }}
            </span>
            <span class="font-bold text-lg">${{ item.finalPrice.toFixed(2) }}</span>
          </div>
          
        </div>
      </div>

    </div>
  </section>
</template>