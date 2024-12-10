<script setup lang="ts">
import CarouselGalery from './components/CarouselGalery.vue';
import GaleryGrid from './components/GaleryGrid.vue';

import type { ICharacter } from '@/interfaces/ICharacter';
import ApiService from '@/service/ApiService';
import { onMounted, ref } from 'vue';
import { VueSpinnerGears } from 'vue3-spinners';
import GaleryFooter from './components/GaleryFooter.vue';

const apiService = new ApiService();

const isLoading = ref(false);

const data = ref<ICharacter[]>([]);

const getData = async () => {
  try {
    isLoading.value = true;
    const response = await apiService.getCharacters();
    data.value = response.results;
  } catch (error) {
    console.error(error);
  } finally {
    isLoading.value = false;
  }
};

onMounted(() => {
  getData();
});
</script>

<template>
  <h1 class="text-center text-4xl p-5 text-[#584f3d]">Galeria Rick & Morty</h1>
  <div v-if="isLoading" class="flex justify-center items-center h-full">
    <VueSpinnerGears size="48" color="#756951" />
  </div>
  <div v-else class="p-2">
    <div class="lg:flex items-center justify-center">
      <CarouselGalery :characters="data" />
    </div>
    <GaleryGrid :characters="data" />
  </div>
  <GaleryFooter />
</template>

<style scoped></style>
