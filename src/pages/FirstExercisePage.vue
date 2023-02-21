<script setup lang="ts">
import { ref } from 'vue'
import CardItem from '../components/CardItem.vue'
import HeaderBanner from '../components/HeaderBanner.vue'
import cards from '../assets/data.json'

const activeCardIndex = ref(0)

function handleActiveChange(index: number): void {
  activeCardIndex.value = index === activeCardIndex.value ? -1 : index
}
</script>

<template>
  <header-banner />

  <Transition appear appear-active-class="fade-enter-up">
    <section class="container-lg card-item">
      <div class="row row-cols-md-2 row-cols-lg-3 gy-3 g-lg-5 card-item__container">
        <CardItem v-for="(card, index) in cards" 
          :title="card.title" 
          :content="card.content" 
          :index="index"
          :is-active="activeCardIndex === index" 
          @button-clicked="handleActiveChange"
        />
      </div>
    </section>
  </Transition>
</template>

<style scoped lang="scss">

.card-item {
  padding: 2rem 1.5rem 2rem 1.5rem;

  &__container {
    justify-content: center;
  }
}

.fade-enter-up {
  animation: fade-enter-up 2s ease-in-out;
}

.fade-in {
  animation: fade-in 1s ease-in-out;
}

@keyframes fade-enter-up {
  from {
    opacity: 50;
    transform: translateY(50%)
  }

  to {
    opacity: 100;
    transform: translateY(0);
  }
}

@keyframes fade-in {
  from {
    opacity: 0;
  }

  to {
    opacity: 1;
  }
}
</style>
