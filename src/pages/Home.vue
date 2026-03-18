<template>
  <v-container class="py-4">
    <v-row justify="center" class="mb-4">
      <v-btn
        v-for="cat in categories"
        :key="cat"
        class="ma-1"
        :variant="selectedCategory === cat ? 'flat' : 'outlined'"
        color="primary"
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
      md="4"
    >
      <ProductCard :product="product" />
    </v-col>
  </v-row>
</v-container>
</template>

<script setup>
import ProductCard from '../components/ProductCard.vue'
import { ref, computed } from 'vue'

const selectedCategory = ref('Todas')

const categories = [
  'Todas',
  'Edição Limitada',
  'Home Spray',
  'Difusores',
  'Velas',
]

// seus produtos aqui (mantém igual)
const products = [
  {
    "id": 1,
    "category": "Edição Limitada",
    "name": "Vela Ovo de Páscoa 100g",
    "price": 45.0,
    "thumbnail": "/images/vela-ovo-small.jpg",
    "image": "/images/vela-ovo.jpg",
    "description": "Vela em recipiente metálico com fragrância exclusiva de Chocolate Belga e Rum. Diversas estampas disponíveis (consulte disponibilidade)."
  },
  {
    "id": 2,
    "category": "Home Spray",
    "name": "Home Spray 100ml",
    "price": 19.9,
    "thumbnail": "/images/home-spray-100-small.jpg",
    "image": "/images/home-spray-100.jpg",
    "description": "Compacto e prático, ideal para levar em viagens e perfumar qualquer ambiente rapidamente."
  },
  {
    "id": 3,
    "category": "Home Spray",
    "name": "Home Spray 225ml",
    "price": 29.9,
    "thumbnail": "/images/home-spray-225-small.jpg",
    "image": "/images/home-spray-225.jpg",
    "description": "Perfuma o ambiente com leveza e rapidez. Pode ser usado no ar ou em tecidos."
  },
  {
    "id": 4,
    "category": "Difusores",
    "name": "Difusor de Varetas 100ml",
    "price": 29.9,
    "thumbnail": "/images/difusor-100-small.jpg",
    "image": "/images/difusor-100.jpg",
    "description": "Frasco de vidro com fragrância suave e equilibrada, ideal para perfumar com delicadeza."
  },
  {
    "id": 5,
    "category": "Difusores",
    "name": "Difusor de Varetas 200ml",
    "price": 55.9,
    "thumbnail": "/images/difusor-200-small.jpg",
    "image": "/images/difusor-200.jpg",
    "description": "Versão maior com maior duração e presença, ideal para ambientes maiores."
  },
  {
    "id": 6,
    "category": "Difusores",
    "name": "Flor Difusora",
    "price": 24.9,
    "thumbnail": "/images/flor-difusora-small.jpg",
    "image": "/images/flor-difusora.jpg",
    "description": "Alternativa delicada às varetas tradicionais, trazendo charme e sofisticação."
  },
  {
    "id": 7,
    "category": "Difusores",
    "name": "Difusor com Flor 100ml",
    "price": 49.9,
    "thumbnail": "/images/difusor-flor-100-small.jpg",
    "image": "/images/difusor-flor-100.jpg",
    "description": "Opção delicada e sofisticada para perfumar ambientes menores."
  },
  {
    "id": 8,
    "category": "Difusores",
    "name": "Difusor com Flor 200ml",
    "price": 75.9,
    "thumbnail": "/images/difusor-flor-200-small.jpg",
    "image": "/images/difusor-flor-200.jpg",
    "description": "Versão maior com mais duração e presença no ambiente."
  },
  {
    "id": 9,
    "category": "Difusores",
    "name": "Refil 500ml",
    "price": 70.0,
    "thumbnail": "/images/refil-500-small.jpg",
    "image": "/images/refil-500.jpg",
    "description": "Refil para manter seu ambiente perfumado com economia e praticidade."
  },
  {
    "id": 10,
    "category": "Velas",
    "name": "Vela Lata 20g",
    "price": 9.0,
    "thumbnail": "/images/vela-lata-small.jpg",
    "image": "/images/vela-lata.jpg",
    "description": "Compacta e minimalista, perfeita para pequenos ambientes."
  },
  {
    "id": 11,
    "category": "Velas",
    "name": "Vela Geleinha 30g",
    "price": 16.0,
    "thumbnail": "/images/vela-geleinha-small.jpg",
    "image": "/images/vela-geleinha.jpg",
    "description": "Charmosa e delicada, ideal para perfumar pequenos espaços."
  },
  {
    "id": 12,
    "category": "Velas",
    "name": "Vela Vidrinho 50g",
    "price": 22.0,
    "thumbnail": "/images/vela-vidrinho-small.jpg",
    "image": "/images/vela-vidrinho.jpg",
    "description": "Visual elegante com tampa de madeira, perfeita para decoração."
  },
  {
    "id": 13,
    "category": "Velas",
    "name": "Vela Pate 90g",
    "price": 30.0,
    "thumbnail": "/images/vela-pate-small.jpg",
    "image": "/images/vela-pate.jpg",
    "description": "Elegante e acolhedora, com visual natural e atemporal."
  },
  {
    "id": 14,
    "category": "Velas",
    "name": "Vela Mini Belém 100g",
    "price": 30.0,
    "thumbnail": "/images/vela-belem-small.jpg",
    "image": "/images/vela-belem.jpg",
    "description": "Compacta e versátil, com presença suave e elegante."
  },
  {
    "id": 15,
    "category": "Velas",
    "name": "Vela Pianezza 130g",
    "price": 40.0,
    "thumbnail": "/images/vela-pianezza1-small.jpg",
    "image": "/images/vela-pianezza1.jpg",
    "description": "Design sofisticado que une fragrância e decoração."
  },
  {
    "id": 16,
    "category": "Velas",
    "name": "Vela Pianezza 150g",
    "price": 45.0,
    "thumbnail": "/images/vela-pianezza2-small.jpg",
    "image": "/images/vela-pianezza2.jpg",
    "description": "Elegante e acolhedora, perfeita para criar ambientes aconchegantes."
  },
  {
    "id": 17,
    "category": "Velas",
    "name": "Vela Whisky 200g",
    "price": 52.0,
    "thumbnail": "/images/vela-whisky-small.jpg",
    "image": "/images/vela-whisky.jpg",
    "description": "Design robusto com presença marcante e sofisticada."
  },
  {
    "id": 18,
    "category": "Velas",
    "name": "Vela Pianezza 300g",
    "price": 60.0,
    "thumbnail": "/images/vela-pianezza3-small.jpg",
    "image": "/images/vela-pianezza3.jpg",
    "description": "Grande e sofisticada, ideal para ambientes amplos."
  }
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