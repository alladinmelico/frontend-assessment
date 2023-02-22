<script setup lang="ts">
import type { DataItem } from '../interfaces'
import PlusIcon from '../components/PlusIcon.vue'
import MinusIcon from '../components/MinusIcon.vue'

defineProps<{
  data: DataItem[]
  activeItemIndex: number
}>()

defineEmits<{ (e: "button-clicked", id: number): void }>()
</script>

<template>
  <div class="accordion">
    <div v-for="(item, index) in data" class="accordion__item">
      <div @click="$emit('button-clicked', index)" class="accordion__item__title"
        :class="activeItemIndex === index && 'accordion__item--active'">
        {{ item.title }}
        <minus-icon v-if="activeItemIndex === index" />
        <plus-icon v-else />
      </div>
      <div v-if="activeItemIndex === index" class="accordion__item__content" v-html="item.content">
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.accordion {
  margin: 0 1rem 3rem 1rem;
  padding: 1rem;
  width: 100%;

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
</style>