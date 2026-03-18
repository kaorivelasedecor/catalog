<template>
  <v-card elevation="1" rounded="lg">

    <v-img
      :src="product.image"
      height="350px"
      cover
    />

    <v-card-item>
      <v-card-title class="text-h6">
        {{ product.name }}
      </v-card-title>

      <v-card-subtitle class="text-grey-darken-1">
        {{ product.description }}
      </v-card-subtitle>
    </v-card-item>

    <v-card-actions class="d-flex justify-space-between align-center">
      <span class="text-h6 font-weight-bold">
        R$ {{ product.price }}
      </span>

      <v-btn
        color="green"
        variant="flat"
        @click="buyOnWhatsApp"
      >
        Comprar
      </v-btn>
    </v-card-actions>

  </v-card>
</template>

<script setup>
const props = defineProps({
  product: Object
})

function buyOnWhatsApp() {
  const message = `Olá! Tenho interesse no produto: ${props.product.name}`
  const url = `https://wa.me/5511984380478?text=${encodeURIComponent(message)}`
  window.open(url, '_blank')
}
</script>