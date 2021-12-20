<template>
  <div id="site-container">
    <Navigation>
      <NavigationBtn to="/" icon="home" text="Home" />
      <NavigationBtn to="/a-propos" icon="about" text="À propos" />
    </Navigation>

    <main>
      <router-view v-slot="{ Component }">
        <transition mode="out-in" name="slide">
          <component :is="Component"></component>
        </transition>
      </router-view>
    </main>
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

  main {
    @include theme() {
      background:
          linear-gradient( rgba(0, 11, 62, .3) 100%, rgba(0, 11, 62, .3)100%),
          url('./assets/img/' + theme-get('bg-url')) no-repeat top center / cover;
    }

    flex: 1;
    min-height: 100vh;
    position: relative;
    overflow: hidden;
  }

  .slide-enter-active,
  .slide-leave-active {
    transition: all .5s ease-out;
    .tag {
      transition: all .5s ease-out;
    }
  }

  .slide-enter-from {
    position: absolute;
    left: -100%;

    .tag {
      left: 0px;
      top: 356px;
    }
  }

  .slide-enter-to {
    position: absolute;
    left: 0;

    .tag {
      left: 80px;
      top: 42px;
    }
  }

  .slide-leave-from {
    position: absolute;
    left: 0;
  }

  .slide-leave-to {
    position: absolute;
    left: -100%;
  }

</style>
