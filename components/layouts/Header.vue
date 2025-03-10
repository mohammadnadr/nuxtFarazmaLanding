<template>
  <v-app-bar color="primary" dark :class="isRTL ? 'rtl' : 'ltr'">
    <MainLogo/>
    <v-btn to="/" nuxt>Home</v-btn>
    <v-btn to="/about" nuxt>About</v-btn>
    <v-spacer></v-spacer>
    <LanguageSwitcher/>

  </v-app-bar>
</template>

<script setup>
import {computed} from "vue";
import {useI18n} from "vue-i18n";
const { locale } = useI18n();
const isRTL = computed(() => locale.value === 'fa');

</script>

<style scoped>

</style>