<template>
  <div dir="rtl">

  <NuxtLayout >
    <v-app>
      <NuxtPage />
    </v-app>
  </NuxtLayout>
  </div>

</template>

<script setup>
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
// import { useI18n } from 'vue-i18n';
// import { computed } from 'vue';
//
// const { locale } = useI18n();
//
// const isRTL = computed(() => locale.value === 'fa');
</script>
