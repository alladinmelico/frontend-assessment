<script setup lang="ts">
import { ref, computed, onMounted, onUnmounted } from 'vue'
import data from '../assets/data.json'
import TabsComponent from '../components/TabsComponent.vue'
import AccordionComponent from '../components/AccordionComponent.vue'

const MAX_WIDTH_ON_MOBILE = 720
const isOnMobile = ref(true)
const activeItemIndex = ref(0)

const selectedItem = computed(() => data[activeItemIndex.value])

function windowResized() {
  isOnMobile.value = window.innerWidth < MAX_WIDTH_ON_MOBILE
}

function handleActiveChange(index: number): void {
  activeItemIndex.value = index === activeItemIndex.value ? -1 : index
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
    <accordion-component 
      v-if="isOnMobile" 
      :data="data" 
      :active-item-index="activeItemIndex"
      @button-clicked="handleActiveChange"
    />
    <div v-else class="container-sm">
      <tabs-component 
        :data="data" 
        :active-item-index="activeItemIndex"
        :selected-item="selectedItem"
        @button-clicked="handleActiveChange"
      />
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
</style>
