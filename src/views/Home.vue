<template>
  <main class="home">
    <h2>Julien Paris</h2>
    <JPTyping is-loop :typed-speed="30" :wait-time="3000" :strings="['Développeur web fullstack', 'Ceci est un test']" />
  </main>
</template>

<script setup lang="ts">
import JPTyping from '@/components/jp-typing/JPTyping.vue';
</script>

<style scoped lang="scss">
.home {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  h2, p {
    @include theme() {
      color: theme-get('text-color');
    }
    font-family: 'Oxygen', sans-serif;
  }

  h2 {
    font-weight: bold;
    font-size: 4rem;
  }

  p {
    font-weight: 200;
    font-size: 2rem;
  }
}
</style>
