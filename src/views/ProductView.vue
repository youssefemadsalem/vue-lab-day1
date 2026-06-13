<script setup>
import { computed, onMounted, onUnmounted } from 'vue'
import { useRoute } from 'vue-router'
import ProductDetails from '../components/ProductDetails.vue'
import ProductCard from '../components/ProductCard.vue'

const props = defineProps({
  products: {
    type: Array,
    required: true
  }
})

const emit = defineEmits(['buy'])
const route = useRoute()

// Computed properties automatically update if the route ID changes
const currentProduct = computed(() => {
  return props.products.find(p => p.id === Number(route.params.id))
})

const relatedProducts = computed(() => {
  return props.products.filter(p => p.id !== Number(route.params.id))
})

onMounted(() => console.log(`ProductView mounted for ID: ${route.params.id}`))
onUnmounted(() => console.log('ProductView unmounted'))
</script>

<template>
  <div v-if="currentProduct" class="flex flex-col gap-10">
    <ProductDetails :product="currentProduct" @buy="(id) => emit('buy', id)" />

    <section>
      <h3 class="text-2xl font-bold mb-4">Related Products</h3>
      <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
        <ProductCard 
          v-for="product in relatedProducts" 
          :key="product.id" 
          :product="product" 
        />
      </div>
    </section>
  </div>
  <div v-else class="text-center py-20 text-error font-bold text-2xl">
    Product not found!
  </div>
</template>