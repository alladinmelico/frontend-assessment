<script setup lang="ts">
import { ref, computed, onMounted, onUnmounted } from 'vue'
import HeaderBanner from '../components/HeaderBanner.vue'
import data from '../assets/data.json'
import PlusIcon from '../components/PlusIcon.vue'
import MinusIcon from '../components/MinusIcon.vue'

const MAX_WIDTH_ON_MOBILE = 720
const isOnMobile = ref(true)
const activeItemIndex = ref(0)

const selectedItem = computed(() => data[activeItemIndex.value])

function windowResized() {
  isOnMobile.value = window.innerWidth < MAX_WIDTH_ON_MOBILE
}

onMounted(() => {
  window.addEventListener('resize', windowResized)
  windowResized()
})
onUnmounted(() => {
  window.addEventListener('resize', windowResized)
})
</script>

<template>
  <section class="second-exercise-container">
    <div v-if="isOnMobile" class="accordion">
      <div v-for="(item, index) in data" class="accordion__item">
        <div @click="activeItemIndex = index" class="accordion__item__title"
          :class="activeItemIndex === index && 'accordion__item--active'">
          {{ item.title }}
          <minus-icon v-if="activeItemIndex === index" />
          <plus-icon v-else />
        </div>
        <div v-if="activeItemIndex === index" class="accordion__item__content" v-html="item.content">
        </div>
      </div>
    </div>
    <div v-else class="container-sm">
      <div class="tabs">
        <div v-for="(item, index) in data" class="tabs__item" :class="activeItemIndex === index && 'tabs--active'"
          @click="activeItemIndex = index">
          {{ item.title }}
        </div>
      </div>
      <div class="tabs-content" v-html="selectedItem.content"></div>
    </div>
  </section>
</template>

<style scoped lang="scss">
.second-exercise-container {
  display: flex;
  width: 100%;
  height: 100vh;
  justify-content: center;
  align-items: center;
}
.accordion {
  margin: 1rem;
  padding: 1rem;

  &__item {
    margin-top: 1rem;
    cursor: pointer;

    &__title {
      display: flex;
      justify-content: space-between;
      padding: 1rem 1rem 0.5rem 0;
      border-bottom: 1px solid rgb(201, 201, 201);
      color: rgb(133, 133, 133);

      &:hover {
        color: var(--secondary-color);
        padding-bottom: 1rem;
      }

      &__arrow {
        height: 1.5rem;
        width: 1.5rem;
      }

      img {
        height: 1rem;
        width: 1rem;
        color: red;
      }
    }

    &--active {
      border-color: var(--primary-color);
      color: var(--primary-color);
      padding-bottom: 1rem;
      font-weight: 900;
      border-width: 3px;

      &:hover {
        color: var(--primary-color);
      }
    }

    &__content {
      padding-top: 0.5rem;
      padding-bottom: 1rem;
    }
  }
}

.tabs {
  margin-top: 2rem;
  display: flex;
  -webkit-box-shadow: inset 0px -3px 0px 0px rgba(215, 215, 215, 0.401);
  -moz-box-shadow: inset 0px -3px 0px 0px rgba(215, 215, 215, 0.401);
  box-shadow: inset 0px -3px 0px 0px rgba(215, 215, 215, 0.401);

  &__item {
    padding: 1rem;
    color: var(--primary-color);
    cursor: pointer;

    &:hover {
      font-weight: 900;
    }
  }

  &--active {
    border-bottom: 3px solid var(--primary-color);
    color: var(--secondary-color);
    font-weight: 900;
  }
}

.tabs-content {
  padding-top: 1rem;
  padding-bottom: 3rem;
}</style>
