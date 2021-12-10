<template>
    <div class="navbar">
      <header class="navbar__header">
        <img src="@/assets/img/sidenav-profile-picture.png" alt="Profile Picture Julien Paris">
        <h1>Julien <span>Paris</span></h1>
      </header>

      <nav class="navbar__navigation">
        <slot></slot>
      </nav>
    </div>
</template>

<script setup lang="ts">
</script>

<style scoped lang="scss">
.navbar {
  @include theme() {
    background-color: theme-get('bg-color');
  }
  overflow-y: auto;
  // Firfox scrollbar rules
  scrollbar-width: auto;
  scrollbar-color: #7e79ff #ffffff;
  // Chrome, edge, safari
  &::-webkit-scrollbar { width: 16px; }
  &::-webkit-scrollbar-track { background: #ffffff; }
  &::-webkit-scrollbar-thumb {
    background-color: #7e79ff;
    border-radius: 10px;
    border: 3px solid #ffffff;
  }

  width: 160px;
  height: 100vh;
  box-shadow: 0 19px 38px rgba(0,0,0,0.30), 0 15px 12px rgba(0,0,0,0.22);

  &__header {
    @include theme() {
      border-bottom: 1px solid lighten(theme-get('nav-text-color'), 20);
    }

    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 32px 0;

    h1 {
      @include theme() {
        color: theme-get('title-color');
      }

      font-family: 'Oxygen', sans-serif;
      font-size: 28px;
      font-weight: 200;

      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      padding-top: 12px;

      span {
        font-weight: 400;
      }
    }
  }
}
</style>
