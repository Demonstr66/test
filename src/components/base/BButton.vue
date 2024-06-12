<script setup>
  defineProps({
    outlined: {
      type: Boolean,
      default: false
    },
    icon: {
      type: Boolean,
      default: false
    }
  })
</script>

<template>
  <button :class="['b-btn', 'b-btn--red', {'b-btn--outlined': outlined || icon, 'b-btn--icon': icon}]">
    <slot />
  </button>
</template>

<style lang="scss">
  $btn-size: 42px;

  .b-btn {
    height: $btn-size;
    border-radius: 6px;
    padding: 9px;
    width: fit-content;
    color: #FFFFFF;

    font-size: 12px;
    font-weight: 700;
    line-height: 20px;
    text-align: left;
    text-transform: uppercase;
    letter-spacing: 1px !important;

    cursor: pointer;
    transition: all 0.3s ease-in-out;

    &--red {
      background-color: #D90E32;
      border-color: #D90E32;

      &:hover {
        background-color: rgba(217, 14, 50, 0.75);
      }
    }

    &--outlined {
      background-color: transparent !important;
      border-width: 1px;
      border-style: solid;

      &:hover {
        background-color: rgba(217, 14, 50, 0.15) !important;
      }
    }

    &--icon {
      width: $btn-size;
    }
  }
</style>