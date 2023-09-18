<template>
  <main>
    <card
      v-for="(card, index) in cards"
      :key="index"
      :front-url="card.frontUrl"
      :class="{ flipped: card.isFlipped }"
    />
  </main>
  <button @click="cards[1].isFlipped = !cards[1].isFlipped">Flip</button>
</template>

<script setup lang="ts">
import { reactive } from 'vue';
import Card from '@/components/Card.vue';

interface Card {
  frontUrl?: string;
  isFlipped: boolean;
}

const cards = reactive<Array<Card>>([{ isFlipped: false }, { isFlipped: false, frontUrl: "club_2.jpg" }, { isFlipped: false }]);

</script>

<style scoped>
main {
  display: flex;
  width: 80%;
  margin: 0 auto;
}

button {
  display: block;
  width: 100px;
  height: 30px;
  border-radius: 5px;
  cursor: pointer;
  margin: 20px auto;
  border: none;
}

@media (max-width: 481px) {
  main {
    flex-direction: column;
  }
}

</style>