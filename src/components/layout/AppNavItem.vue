<script setup>
  defineProps({
    active: {
      type: Boolean,
      default: false
    }
  })
</script>

<template>
  <div class="nav-item" :class="{'nav-item--active': active}">
    <div v-if="active" class="active-bar"></div>
    <slot />
  </div>
</template>

<style lang="scss">
  .nav-item {
    position: relative;
    display: flex;
    align-items: center;
    gap: 20px;
    height: 48px;
    padding: 12px 30px;

    color: rgba(255, 255, 255, 0.45);

    &--active {
      padding-left: 32px;
      background-color: rgba(255, 255, 255, 0.2);
    }
  }

  .active-bar {
    position: absolute;
    left: 0;
    top: 0;
    bottom: 0;
    width: 2px;
    background-color: #D90E32;
  }
</style>