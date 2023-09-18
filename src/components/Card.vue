<template>
  <div class="card">
    <div class="cover front"></div>
    <div class="cover back" :style="{ backgroundImage: `url(/src/assets/images/${props.frontUrl})` }"></div>
  </div>
</template>

<script setup lang="ts">

import { defineProps } from 'vue';

const props = defineProps<{
  frontUrl?: string;
}>();

</script>

<style scoped lang="scss">
.card {
  width: 230px;
  height: 300px;
  transform-style: preserve-3d;
  transition: all 0.8s ease;

  .cover {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    border-radius: 15px;
    backface-visibility: hidden;
    overflow: hidden;
    background-size: cover;

    &.front {
      background-image: url('@/assets/images/back.jpg');
    }

    &.back {
      transform: rotateY(180deg);
    }
  }

  &.flipped {
    transform: rotateY(180deg) translateY(-320px);
  }

  &:not(:first-child) {
    margin-left: 30px;
  }
}

@media (max-width: 769px) {
  .card {
    width: 127px;
    height: 200px;

    &.flipped {
      transform: rotateY(180deg) translateY(-210px);
    }
  }
}

@media (max-height: 769px) {
  .card.flipped {
    transform: rotateY(180deg) translateY(-280px);
  }
}

@media (max-width: 481px) {
  .card {
    width: 127px;
    height: 200px;

    &:not(:first-child) {
      margin-left: 0;
      margin-top: 10px;
    }

    &.flipped {
      transform: rotateY(180deg) translateX(-130px);
    }
  }
}

</style>