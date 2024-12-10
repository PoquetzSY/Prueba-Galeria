<script setup lang="ts">
import type { ICharacter } from '@/interfaces/ICharacter';
import { ref } from 'vue';

interface Props {
  character: ICharacter;
  propClass?: string;
  textClass?: string;
  imgClass?: string;
}

const props = defineProps<Props>();

const character = ref<ICharacter>(props.character);
</script>

<template>
  <div :class="propClass" class="bg-[#BBE0F2] rounded-lg shadow-md hover:bg-[#AEE6E3]">
    <img
      :src="character.image"
      :alt="character.name"
      :class="imgClass"
      class="w-full object-cover rounded-t-lg"
    />
    <div class="p-4">
      <h2 :class="textClass" class="text-[#3b362d]">{{ character.name }}</h2>
      <p :class="textClass" class="text-gray-600">
        {{ character.species }} - {{ character.status }}
      </p>
    </div>
  </div>
</template>

<style scoped></style>
