<template>
    <Navigation>
      <NavigationBtn />
      <NavigationBtn />
      <NavigationBtn />
      <NavigationBtn />
      <NavigationBtn />
    </Navigation>

  <main>
    <router-view/>
  </main>
</template>

<script setup lang="ts">
import Navigation from "@/components/navigation/Navigation";
import NavigationBtn from '@/components/navigation/NavigationBtn';

</script>

<style lang="scss">
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
</style>
