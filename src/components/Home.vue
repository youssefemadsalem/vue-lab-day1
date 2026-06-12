<script setup>
import { ref, computed } from 'vue'


const mainProduct = ref({
  id: 1,
  name: "Cozy Sneakers",
  description: "High-quality sneakers that go with everything you wear.",
  image: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQfrFEqDIL8NLQXflNotUOO6HAC06mIVpKZ-GhJvXL3hXq5B0Ta88Eyq_w&s=10",
  badge: "NEW",
  price: 120,
  discount: 20,
  tags: ["Fashion", "Casual", "Sport"],
  isAvailable: true 
})

const relatedProducts = ref([
  { id: 2, name: "Running Shoes", price: 90, discount: 10, image: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSvquKtGe1ix78z_HYRPoArF-4pBltRtzenWGSzcvBRAw&s=10" },
  { id: 3, name: "Casual Boots", price: 150, discount: 0, image: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRcIVaAztfvSp7rkdy_GEQK1q4IxrJb50R1bIYQlZRE9m3LsHtcBQKFm8A&s=10" },
  { id: 4, name: "Flip Flops", price: 30, discount: 50, image: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcR0U-C6JukbDrrp4UKzfy1zj6TwK0uSEcZOyUFt5K-x2Q&s=10" }
])


const discountedPrice = computed(() => {
  const discountAmount = mainProduct.value.price * (mainProduct.value.discount / 100);
  return mainProduct.value.price - discountAmount;
})

const relatedProductsWithPrices = computed(() => {
  return relatedProducts.value.map(product => {
    const discountAmount = product.price * (product.discount / 100);
    return {
      ...product,
      finalPrice: product.price - discountAmount
    }
  })
})
</script>

<template>
  <div class="flex flex-col gap-8">
    
    <section class="card lg:card-side bg-base-100 shadow-xl border border-base-300">
      <figure class="lg:w-1/2 p-4">
        <img :src="mainProduct.image" :alt="mainProduct.name" class="rounded-xl w-full object-cover" />
      </figure>
      
      <div class="card-body lg:w-1/2">
        <h2 class="card-title text-3xl">
          {{ mainProduct.name }}
          <div v-if="mainProduct.badge" :class="['badge badge-secondary', {'badge-error': !mainProduct.isAvailable}]">
            {{ mainProduct.isAvailable ? mainProduct.badge : 'Out of Stock' }}
          </div>
        </h2>
        
        <p class="text-gray-500">{{ mainProduct.description }}</p>

        <div class="flex gap-2 my-2">
          <span v-for="(tag, index) in mainProduct.tags" :key="index" class="badge badge-outline">
            {{ tag }}
          </span>
        </div>

        <div class="my-4">
          <span v-if="mainProduct.discount > 0" class="text-lg text-gray-400 line-through mr-2">
            ${{ mainProduct.price.toFixed(2) }}
          </span>
          <span class="text-3xl font-bold text-success">${{ discountedPrice.toFixed(2) }}</span>
        </div>

        <div class="card-actions justify-end mt-auto">
          <button class="btn btn-primary" :disabled="!mainProduct.isAvailable">
            Add to Cart
          </button>
        </div>
      </div>
    </section>

    <section>
      <h3 class="text-2xl font-bold mb-4">Related Products</h3>
      <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
        
        <div v-for="product in relatedProductsWithPrices" :key="product.id" class="card bg-base-100 shadow-sm border border-base-200">
          <figure class="px-4 pt-4">
            <img :src="product.image" :alt="product.name" class="rounded-xl" />
          </figure>
          <div class="card-body items-center text-center">
            <h4 class="card-title text-lg">{{ product.name }}</h4>
            
            <div>
               <span v-if="product.discount > 0" class="text-sm text-gray-400 line-through mr-2">
                ${{ product.price.toFixed(2) }}
              </span>
              <span class="font-bold text-lg">${{ product.finalPrice.toFixed(2) }}</span>
            </div>
            
          </div>
        </div>

      </div>
    </section>

  </div>
</template>