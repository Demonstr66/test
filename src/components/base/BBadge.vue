<script setup>

</script>

<template>
  <div class="badge">
    <slot />
  </div>
</template>

<style lang="scss">
.badge {
  padding: 4px 14px 4px 14px;
  gap: 10px;
  border-radius: 6px;
  background: #F3F6F8;
  width: fit-content;
  height: fit-content;

  font-size: 15px;
  font-weight: 700;
  line-height: 22px;
  text-align: center;
  color: #293148CC;
}
</style>