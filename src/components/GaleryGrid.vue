<script setup lang="ts">
import CharacterCard from './CharacterCard.vue';

import type { ICharacter } from '@/interfaces/ICharacter';
import { ref } from 'vue';

interface Props {
  characters: ICharacter[];
}

const props = defineProps<Props>();

const characters = ref<ICharacter[]>(props.characters);
</script>

<template>
  <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 p-4">
    <div v-for="character in characters" :key="character.id">
      <CharacterCard
        :character="character"
        prop-class="hover:transform hover:-translate-y-3 transition-transform"
        img-class="h-64"
        text-class="text-xl font-semibold"
      />
    </div>
  </div>
</template>

<style scoped></style>
