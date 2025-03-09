<template>
  <v-menu offset-y>
    <template v-slot:activator="{ props }">
      <v-btn icon v-bind="props">
        <v-icon>mdi-translate</v-icon>
      </v-btn>
    </template>
    <v-list>
      <v-list-item
          v-for="(locale, index) in availableLocales"
          :key="index"
          @click="changeLocale(locale.value)"
      >
        {{ locale.title }}
      </v-list-item>
    </v-list>
  </v-menu>
</template>

<script setup lang="ts">
import { useI18n } from 'vue-i18n';
import { useRoute, useRouter } from 'vue-router';
import { computed } from 'vue';
import { useCookie } from 'nuxt/app';

const { locale, setLocale, switchLocalePath } = useI18n();
const route = useRoute();
const router = useRouter();
const cookie = useCookie('currentLocale');

const availableLocales = computed(() => {
  return [
    { title: 'English', value: 'en' },
    { title: 'فارسی', value: 'fa' }
  ];
});

const changeLocale = (newLocale: string) => {
  setLocale(newLocale);
  cookie.value = newLocale;

  // ریدایرکت به صفحه مربوط به زبان جدید
  if (switchLocalePath) {
    const path = switchLocalePath(newLocale);
    router.push(path);
  }
};
</script>