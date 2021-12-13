<template>
  <div class="content">
    <slot></slot>
  </div>
</template>

<script setup lang="ts">
</script>

<style scoped lang="scss">
.content {
  @include theme() {
    background-color: theme-get('bg-color');
  }

  position: absolute;
  top: 42px;
  left: 42px;
  right: 42px;
  bottom: 42px;
  max-width: 1280px;
  margin: 0 auto;
}
</style>
