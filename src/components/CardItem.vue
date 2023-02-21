<script setup lang="ts">
interface Card {
  title: string
  content: string
  image?: string
  isActive: boolean
  index: number
}

defineProps<Card>()

defineEmits<{ (e: "button-clicked", id: number): void }>()
</script>

<template>
  <div class="gy-5">
    <div class="card-item__card">
      <img :src="image || 'https://via.placeholder.com/400x300'" :alt="title" />
      <div class="card-item__card__content">
        <div v-html="content" :class="isActive || 'card-item__card__content--inactive'"></div>
        <div v-if="!isActive" class="card-item__card__content--fade"></div>
      </div>
      <button type="button" @click="$emit('button-clicked', index)">
        {{ isActive ? "Close" : "Read More" }}
      </button>
    </div>
  </div>
</template>

<style scoped lang="scss">
.card-item__card {
  height: 100%;
  min-width: 250px;
  padding: 1rem;
  border-radius: 0.5rem;
  text-align: center;
  box-shadow: 0px 0px 10px 1px rgba(153, 153, 153, 0.19);
  -webkit-box-shadow: 0px 0px 10px 1px rgba(153, 153, 153, 0.19);
  -moz-box-shadow: 0px 0px 10px 1px rgba(153, 153, 153, 0.19);

  &:hover {
    box-shadow: 0px 0px 5px 0.5px rgba(153, 153, 153, 0.4);
    -webkit-box-shadow: 0px 0px 5px 0.5px rgba(153, 153, 153, 0.4);
    -moz-box-shadow: 0px 0px 5px 0.5px rgba(153, 153, 153, 0.4);
  }

  &__content {
    margin: 1rem;
    position: relative;

    &--inactive {
      max-height: 80px;
      display: block;
      overflow: hidden;
    }

    &--fade {
      height: 80px;
      width: 100%;
      background-image: linear-gradient(to bottom, transparent, white);
      position: absolute;
      top: 0;
      left: 0;
    }
  }

  button {
    padding: 0.5rem 1rem 0.5rem 1rem;
    border-radius: 2rem;
    background-color: white;
    border: solid 3px black;
    text-transform: uppercase;
    color: black;
    font-weight: 800;
    margin: 1rem;

    &:hover {
      color: white;
      background-color: black;
    }
  }

  img {
    width: 100%;
    border-radius: 0.25rem;
  }

  p {
    margin-top: 1rem;
  }
}
</style>
