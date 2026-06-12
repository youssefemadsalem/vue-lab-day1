<script setup>
import { ref } from 'vue'


import MainProduct from './MainProduct.vue'
import RelatedProducts from './RelatedProducts.vue'


const mainProductData = ref({
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

const relatedProductsData = ref([
  { id: 2, name: "Running Shoes", price: 90, discount: 10, image: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSvquKtGe1ix78z_HYRPoArF-4pBltRtzenWGSzcvBRAw&s=10" },
  { id: 3, name: "Casual Boots", price: 150, discount: 0, image: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRcIVaAztfvSp7rkdy_GEQK1q4IxrJb50R1bIYQlZRE9m3LsHtcBQKFm8A&s=10" },
  { id: 4, name: "Flip Flops", price: 30, discount: 50, image: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcR0U-C6JukbDrrp4UKzfy1zj6TwK0uSEcZOyUFt5K-x2Q&s=10" }
])
</script>

<template>
  <div class="flex flex-col gap-8">
    
    <MainProduct :product="mainProductData" />

    <RelatedProducts :products="relatedProductsData" />

  </div>
</template>