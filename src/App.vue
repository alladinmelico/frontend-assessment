<script setup lang="ts">
import { ref, computed } from 'vue'
import FirstExercisePage from './pages/FirstExercisePage.vue'
import SecondExercisePage from './pages/SecondExercisePage.vue'

const routes = new Map()
routes.set('first-exercise', FirstExercisePage)
routes.set('second-exercise', SecondExercisePage)

const currentPath = ref(window.location.hash)

window.addEventListener('hashchange', () => {
  currentPath.value = window.location.hash
})

const currentView = computed(() => {
  return routes.get(currentPath.value.slice(1))
})
</script>

<template>
  <section class="nav">
    <div class="nav__bar">
      <div class="nav__bar__title">
        <strong>MindArc's</strong>
        <h1><a href="https://github.com/mindarc/frontend-assessment"> Frontend Developer Assessment</a></h1>
      </div>
      <div class="nav__bar__links">
        <a href="/#first-exercise" class="nav__bar__links__item"
          :class="currentPath === '#first-exercise' && 'nav__bar__links--active'">Exercise 1</a>
        <a href="/#second-exercise" class="nav__bar__links__item"
          :class="currentPath === '#second-exercise' && 'nav__bar__links--active'">Exercise 2</a>
      </div>
    </div>
  </section>
  <component :is="currentView" />
</template>

<style scoped lang="scss">
#app {
  text-align: center;
}

.nav {
  position: absolute;
  min-height: 100px;
  width: 100%;
  z-index: 99;

  &:hover .nav__bar {
    transform: translateY(0);
  }

  &__bar {
    width: 100%;
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
    padding-left: 1rem;
    padding-right: 1rem;
    transform: translateY(-100%);
    transition: transform .5s cubic-bezier(.4, 0, .2, 1);
    background-color: var(--secondary-color);
    transform: translateY(-100%);

    &__title {
      color: white;

      a {
        text-decoration: none;
        color: var(--primary-color);
      }
    }

    &__links {
      display: flex;

      &__item {
        padding: 1rem;
        margin: 1rem;
        border-radius: 0.5rem;
        border: 2px solid rgb(45, 45, 45);
        color: white;
        text-decoration: none;
        text-transform: uppercase;
        font-weight: 900;

        &:hover {
          border-color: var(--primary-color);
        }
      }

      &--active {
        background-color: var(--primary-color);
        color: var(--secondary-color);
        border-color: white;
      }
    }
  }
}
</style>
