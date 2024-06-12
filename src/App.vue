<script setup>
import AppSidebar from "@/components/layout/AppSidebar.vue";
import AppHeader from "@/components/layout/AppHeader.vue";
</script>

<template>
  <app-sidebar />
  <div class="main">
    <app-header class="mt-30"/>
    <router-view/>
  </div>
</template>



<style lang="scss">
#app {
  position: relative;
  min-height: 100vh;

  display: flex;
}

.main {
  flex-grow: 1;
  margin-left: 256px;
}
</style>