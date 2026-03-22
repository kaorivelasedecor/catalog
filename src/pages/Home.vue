<template>
  <v-container class="py-4">
    <v-row justify="center" class="mb-4">
      <v-btn
        v-for="cat in categories"
        :key="cat"
        class="ma-1"
        :variant="selectedCategory === cat ? 'flat' : 'outlined'"
        color="white"
        @click="selectedCategory = cat"
      >
        {{ cat }}
      </v-btn>
    </v-row>
  </v-container>

  <v-container class="py-8">
  <v-row>
    <v-col
      v-for="product in filteredProducts"
      :key="product.id"
      cols="12"
      sm="6"
      md="3"
    >
      <ProductCard :product="product" />
    </v-col>
  </v-row>
</v-container>
</template>

<script setup>
import ProductCard from '../components/ProductCard.vue'
import { ref, computed } from 'vue'
import { products } from '../data/products'

const selectedCategory = ref('Todas')

const categories = [
  'Todas',
  'Edição Limitada',
  'Home Spray',
  'Difusores',
  'Velas',
]

const filteredProducts = computed(() => {
  if (selectedCategory.value === 'Todas') {
    return products
  }

  return products.filter(
    p => p.category === selectedCategory.value
  )
})
</script>
