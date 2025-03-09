<template>
  <v-app>
    <Header/>
    <v-main>
      <v-container  >
        <slot />
      </v-container>
    </v-main>
    <Footer/>
  </v-app>
</template>
<script setup lang="ts">
import Footer from "~/components/layouts/Footer.vue";
import Header from "~/components/layouts/Header.vue";
</script>