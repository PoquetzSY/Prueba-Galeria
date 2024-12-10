<script setup lang="ts">
import 'vue3-carousel/dist/carousel.css';
import { Carousel, Slide, Navigation } from 'vue3-carousel';

import type { ICharacter } from '@/interfaces/ICharacter';
import { onMounted, ref } from 'vue';
import CharacterCard from './CharacterCard.vue';

interface Props {
  characters: ICharacter[];
}

const props = defineProps<Props>();

const screenWidth = ref(window.innerWidth);
const cardsToShow = ref(1);
const characters = ref<ICharacter[]>(props.characters);

const rezise = () => {
  screenWidth.value = window.innerWidth;
  if (screenWidth.value < 640) {
    cardsToShow.value = 1.75;
  } else if (screenWidth.value < 1024) {
    cardsToShow.value = 2.75;
  } else {
    cardsToShow.value = 3.95;
  }
};

window.addEventListener('resize', () => {
  rezise();
});

const config = {
  itemsToShow: cardsToShow,
  wrapAround: true,
  transition: 500,
  autoplay: 3000,
  mouseDrag: true,
};

onMounted(() => {
  rezise();
});
</script>

<template>
  <Carousel v-bind="config" class="mb-10 lg:w-[90%]">
    <Slide v-for="character in characters" :key="character.id">
      <CharacterCard
        :character="character"
        prop-class="w-[200px] xl:w-[300px] trasition-transform"
        text-class="sm:text-sm md:text-base lg:text-lg xl:text-xl whitespace-nowrap overflow-hidden"
        img-class="h-48"
      />
    </Slide>
    <template #addons>
      <Navigation />
    </template>
  </Carousel>
</template>

<style scoped>
.carousel__slide {
  padding: 5;
}

.carousel__viewport {
  perspective: 2000px;
}

.carousel__track {
  transform-style: preserve-3d;
}

.carousel__slide--sliding {
  transition: 0.5s;
}

.carousel__slide {
  opacity: 0.9;
  transform: rotateY(-20deg) scale(0.9);
}

.carousel__slide--active ~ .carousel__slide {
  transform: rotateY(20deg) scale(0.9);
}

.carousel__slide--prev {
  opacity: 1;
  transform: rotateY(-10deg) scale(0.95);
}

.carousel__slide.carousel__slide--next {
  opacity: 1;
  transform: rotateY(10deg) scale(0.95);
}

.carousel__slide--active {
  opacity: 1;
  transform: rotateY(0) scale(1);
}
</style>
