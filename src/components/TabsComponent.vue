<script setup lang="ts">
import type { DataItem } from '../interfaces'

defineProps<{
  data: DataItem[]
  activeItemIndex: number
  selectedItem?: DataItem
}>()

defineEmits<{ (e: "button-clicked", id: number): void }>()
</script>

<template>
  <div class="tabs">
    <div v-for="(item, index) in data" class="tabs__item" :class="activeItemIndex === index && 'tabs--active'"
      @click="$emit('button-clicked', index)">
      {{ item.title }}
    </div>
  </div>
  <div v-if="selectedItem" class="tabs-content" v-html="selectedItem.content"></div>
</template>

<style lang="scss" scoped>
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
}
</style>