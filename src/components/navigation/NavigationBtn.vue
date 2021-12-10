<template>
  <router-link class="navbtn" :to="to">
      <img :src="require('@/assets/img/icons/'+ icon +'.png')" alt="Home">
      {{ text }}
  </router-link>
</template>

<script setup lang="ts">
import {defineProps} from "vue";

const props = defineProps({
  to: String,
  text: String,
  icon: String
})

</script>

<style scoped lang="scss">
.test {
  color: red;
}

.navbtn {
  @include theme() {
    color: lighten(theme-get('nav-text-color'), 15);
    border-bottom: 1px solid lighten(theme-get('nav-text-color'), 20);
  }

  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px 0;

  font-size: 16px;
  font-family: 'Oxygen', sans-serif;
  font-weight: 400;
  text-decoration: none;

  position: relative;
  overflow: hidden;
  transition: color .2s;

  &::after {
    background-color: transparent;
    content: '';
    width: 8px;
    position: absolute;
    top: 0;
    right: -8px;
    bottom: 0;
    transition: all .2s;
  }

  &:hover {
    @include theme() {
      color: theme-get('nav-text-color');
    }
    transition: color .2s;
    &::after {
      @include theme() {
        background-color: theme-get('nav-text-color');
      }
      right: 0px;
    }
  }

  &.router-link-active {
    @include theme() {
      color: theme-get('nav-text-color');
      &::after {
          background-color: theme-get('nav-text-color');
          right: 0;
      }
    }
  }
}
</style>
