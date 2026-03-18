<template>
  <v-card>
    <v-img :src="product.image" height="300px" />

    <v-card-title>
      {{ product.name }}
    </v-card-title>

    <v-card-subtitle>
      R$ {{ product.price }}
    </v-card-subtitle>

    <v-card-text>
      {{ product.description }}
    </v-card-text>
  </v-card>
</template>

<script setup>
  defineProps({
    product: Object
  })
</script>