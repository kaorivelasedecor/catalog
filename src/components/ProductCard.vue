<template>
  <div>
    <!-- CARD -->
    <v-card
      elevation="2"
      rounded="xl"
      @click="dialog = true"
      style="cursor: pointer"
    >
      <v-img :src="`${baseUrl + product.thumbnail}`" height="300px" contain />

      <v-card-item>
        <v-card-title class="product-title text-body-2 text-md-h6">
          {{ product.name }}
        </v-card-title>

        <v-card-subtitle>
          R$ {{ product.price.toFixed(2) }}
        </v-card-subtitle>
      </v-card-item>
    </v-card>

    <!-- MODAL -->
    <v-dialog v-model="dialog" max-width="500">
      <v-card class="position-relative">
        <!-- BOTÃO X -->
        <v-btn
          icon="mdi-close"
          variant="text"
          class="close-btn"
          @click="dialog = false"
        />

        <v-img
          :src="`${baseUrl + product.image}`"
          :lazy-src="product.thumbnail"
          height="500px"
          contain
          class="transition-image"
        />

        <v-card-title>
          {{ product.name }}
        </v-card-title>

        <v-card-text>
          {{ product.description }}
        </v-card-text>

        <v-card-actions class="justify-space-between">
          <span class="text-h6">
            R$ {{ product.price.toFixed(2) }}
          </span>

          <v-btn color="green" @click="buyOnWhatsApp">
            Comprar
          </v-btn>
        </v-card-actions>

      </v-card>
    </v-dialog>
  </div>
</template>

<script setup>
import { ref } from 'vue'
const baseUrl = import.meta.env.BASE_URL

const dialog = ref(false)

const props = defineProps({
  product: Object
})

function buyOnWhatsApp() {
  const message = `Olá! Tenho interesse no produto: ${props.product.name}`
  const url = `https://wa.me/5511984380478?text=${encodeURIComponent(message)}`
  window.open(url, '_blank')
}
</script>

<style scoped>
.product-title {
  white-space: normal !important;
  overflow: visible !important;
  text-overflow: unset !important;
  display: block !important;
  line-height: 1.2;
}
</style>
