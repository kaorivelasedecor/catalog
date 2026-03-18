<template>
  <v-container class="py-8">
    <v-row>
      <v-col
        v-for="product in products"
        :key="product.id"
        cols="12"
        sm="6"
        md="4"
      >
        <ProductCard :product="product" />
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import ProductCard from '../components/ProductCard.vue'

const products = [
  {
    id: 1,
    name: "Kitten",
    price: 39.9,
    image: "/images/kitten.jpg",
    description: "Cute"
  },
  {
    id: 2,
    name: "Kitten",
    price: 49.9,
    image: "/images/kitten.jpg",
    description: "Cute"
  }
]
</script>