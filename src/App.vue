<template>
  <div id="site-container">
    <Navigation>
      <NavigationBtn to="/" icon="home" text="Home" />
      <NavigationBtn to="/a-propos" icon="about" text="À propos" />
    </Navigation>

    <router-view/>
  </div>
</template>

<script setup lang="ts">
import Navigation from "@/components/navigation/Navigation";
import NavigationBtn from "@/components/navigation/NavigationBtn"
</script>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css2?family=Oxygen:wght@300;400;700&display=swap');

  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  #site-container {
    display: flex;
  }
</style>
