<template>
  <NuxtLayout  >
    <v-app :class="{ 'rtl': isRTL, 'ltr': !isRTL }" >
      <NuxtPage />
    </v-app>
  </NuxtLayout>

</template>

<script setup>
import { computed } from 'vue';

import { useI18n } from 'vue-i18n';
import { useCookie } from 'nuxt/app';

const { locale, setLocale } = useI18n();
const cookie = useCookie('currentLocale');

const initializeLocale = () => {
  if (cookie.value) {
    setLocale(cookie.value);
  }
};

onMounted(() => {
  initializeLocale();
});
const isRTL = computed(() => locale.value === 'fa');
</script>
<style>
</style>