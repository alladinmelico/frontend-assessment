<script setup lang="ts">
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
</template>

<style scoped lang="scss">
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
</style>
