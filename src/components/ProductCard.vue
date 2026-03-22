<template>
  <div>
    <!-- CARD -->
    <v-card
      elevation="2"
      rounded="xl"
      @click="dialog = true"
      style="cursor: pointer"
    >
      <v-img :src="product.thumbnail" height="400px" cover />

      <v-card-item>
        <v-card-title class="text-h6">
          {{ product.name }}
        </v-card-title>

        <v-card-subtitle>
          R$ {{ product.price.toFixed(2) }}
        </v-card-subtitle>
      </v-card-item>
    </v-card>

    <!-- MODAL -->
    <v-dialog v-model="dialog" max-width="500">
      <v-card>

        <v-img
          :src="product.image"
          :lazy-src="product.thumbnail"
          height="500px"
          cover
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
