<script setup>

import BBadge from "@/components/base/BBadge.vue";
import BButton from "@/components/base/BButton.vue";
import AppLangSelect from "@/components/layout/AppLangSelect.vue";

</script>

<template>
  <div class="header">
    <h1 class="h1 mt-4">
      Vechicles
    </h1>
    <b-badge class="mt-8 ml-25">256</b-badge>

    <b-button outlined icon class="ml-566 mt-2">
      <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path fill-rule="evenodd" clip-rule="evenodd" d="M12 4C12.5523 4 13 4.44772 13 5V19C13 19.5523 12.5523 20 12 20C11.4477 20 11 19.5523 11 19V5C11 4.44772 11.4477 4 12 4Z" fill="#E86E84"/>
        <path fill-rule="evenodd" clip-rule="evenodd" d="M4 12C4 11.4477 4.44772 11 5 11H19C19.5523 11 20 11.4477 20 12C20 12.5523 19.5523 13 19 13H5C4.44772 13 4 12.5523 4 12Z" fill="#E86E84"/>
      </svg>
    </b-button>
    <div class="ml-40 avatar">
      <img :src="require('@/assets/img.png')" alt="" />
    </div>
    <div class="ml-14 mt-12 username">
      John Doe
    </div>

    <app-lang-select class="ml-37 mt-11"/>
  </div>
</template>

<style lang="scss">
  .header {
    display: flex;
    height: 72px;
    width: 100%;
    border-bottom: 1px solid #E4E4E4;

    .h1 {
      font-size: 32px;
      font-weight: 700;
      line-height: 38px;
      text-align: left;
      margin-left: 30px;
    }

    .avatar {
      width: 46px;
      height: 46px;
      border-radius: 50%;

      & img {
        width: 100%;
        height: 100%;
      }
    }

    .username {
      font-size: 15px;
      font-weight: 500;
      line-height: 22px;
      text-align: left;
      color: #293148;
      letter-spacing: 0;

    }
  }
</style>