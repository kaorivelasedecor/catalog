<template>
  <v-app>
    <AppHeader />

    <v-main>
      <Home />
    </v-main>
  </v-app>
</template>

<script setup>
  import AppHeader from './components/AppHeader.vue'
  import Home from './pages/Home.vue'
</script>