<template>
  <div class="text-center py-6 bg-white w-100">
    <img
      src="/images/logo-kaori-preto.jpg"
      alt="Kaori"
      style="height: 250px"
    />
  </div>

  <div class="sticky-filter">
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
  </div>

  <v-container class="py-8">
  <v-row>
    <v-col
      v-for="product in filteredProducts"
      :key="product.id"
      cols="6"
      sm="4"
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
  'Edições Especiais',
  'Linha Literária',
  'Extras',
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

<style scoped>
  .sticky-filter {
    position: sticky;
    background: black;
    top: 0;
    z-index: 10;
    padding-top: 32px;
    padding-bottom: 8px;
  }
</style>
