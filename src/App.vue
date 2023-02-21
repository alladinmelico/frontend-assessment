<script setup lang="ts">
import { ref } from 'vue'
import AccordionCard from './components/AccordionCard.vue'
import cards from './assets/data.json'

const activeCardIndex = ref(0)

function handleActiveChange(index: number): void {
  activeCardIndex.value = index === activeCardIndex.value ? -1 : index
}
</script>

<template>
  <section class="container-fluid header">
    <picture class="header__banner">
      <source media="(max-width: 420px)" srcset="https://via.placeholder.com/600x600" />
      <source media="(max-width: 720px)" srcset="https://via.placeholder.com/1920x650" />
      <img src="https://via.placeholder.com/1920x650" alt="Placeholder image" />
    </picture>
    <Transition appear appear-active-class="fade-in">
      <div class="header__text">
        <h1>Hello Developer!</h1>
        <h2>Lorem ipsum dolor sit, amet consectetur adipisicing elit.</h2>
      </div>
    </Transition>
  </section>

  <Transition appear appear-active-class="fade-enter-up">
    <section class="container-lg accordion">
      <div class="row row-cols-md-2 row-cols-lg-3 gy-3 g-lg-5 accordion__container">
        <AccordionCard v-for="(card, index) in cards" 
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
#app {
  margin: 0 auto;
  text-align: center;
}

.header {
  padding: 0;
  position: relative;

  &__banner {
    width: 100%;
    height: 100%;
    display: flex;

    img {
      object-fit: cover;
      height: auto;
      width: 100%;
    }
  }

  &__text {
    text-align: center;
    color: white;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    -webkit-transform: translate(-50%, -50%);

    h1 {
      font-size: 4rem;
      font-weight: 700;
    }
  }
}

.accordion {
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
