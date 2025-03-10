<template>
  <v-app :class="{ 'rtl': isRTL, 'ltr': !isRTL }">
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
import {computed} from "vue";
import {useI18n} from "vue-i18n";
const { locale, setLocale } = useI18n();

const isRTL = computed(() => locale.value === 'fa');

</script>