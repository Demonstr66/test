<script setup>

import AppNavItem from "@/components/layout/AppNavItem.vue";
</script>

<template>
  <div class="sidebar">
    <div class="sidebar__title">
      Demo Test
    </div>

    <nav style="margin-top: 102px; display: flex; flex-direction: column; gap: 16px">
      <app-nav-item>
        <svg width="24" height="25" viewBox="0 0 24 25" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M12 11.5527C14.2091 11.5527 16 9.76187 16 7.55273C16 5.3436 14.2091 3.55273 12 3.55273C9.79086 3.55273 8 5.3436 8 7.55273C8 9.76187 9.79086 11.5527 12 11.5527Z" stroke="white" stroke-opacity="0.45" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          <path d="M16.5 21.6949C17.888 21.445 18.9884 21.0643 19.5 20.5527C19.5719 19.9059 19.5 18.8861 19.5 18.8861C19.5 18.002 19.0786 17.1542 18.3284 16.5291C15.9595 14.5549 8.04053 14.5549 5.67158 16.5291C4.92143 17.1542 4.5 18.002 4.5 18.8861C4.5 18.8861 4.42813 19.9059 4.5 20.5527C5.01157 21.0643 6.11198 21.445 7.5 21.6949" stroke="white" stroke-opacity="0.45" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
        Profile
      </app-nav-item>
      <app-nav-item active>
        <svg width="24" height="25" viewBox="0 0 24 25" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path fill-rule="evenodd" clip-rule="evenodd" d="M12 3.55273C7.86586 3.55273 4.18305 6.86007 3.16847 10.802C3.03081 11.3368 2.48563 11.6588 1.95078 11.5212C1.41592 11.3835 1.09394 10.8383 1.2316 10.3035C2.43723 5.61926 6.81495 1.55273 12 1.55273C18.0751 1.55273 23 6.4776 23 12.5527C23 18.6279 18.0751 23.5527 12 23.5527C6.67713 23.5527 2.2393 19.773 1.22002 14.7517C1.11016 14.2104 1.45986 13.6826 2.0011 13.5727C2.54235 13.4629 3.07018 13.8126 3.18005 14.3538C4.01385 18.4614 7.64704 21.5527 12 21.5527C16.9706 21.5527 21 17.5233 21 12.5527C21 7.58217 16.9706 3.55273 12 3.55273Z" fill="white" fill-opacity="0.45"/>
          <circle cx="12" cy="12.5527" r="6" stroke="white" stroke-opacity="0.45" stroke-width="2"/>
          <circle cx="12" cy="12.5527" r="1" stroke="white" stroke-opacity="0.45" stroke-width="2"/>
        </svg>
        Vechicles
      </app-nav-item>
      <app-nav-item>
        <svg width="24" height="25" viewBox="0 0 24 25" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M3 12.5528V16.5528C3.00036 16.9035 3.09294 17.2479 3.26846 17.5516C3.44398 17.8552 3.69626 18.1074 4 18.2828L11 22.2828C11.304 22.4583 11.6489 22.5507 12 22.5507C12.3511 22.5507 12.696 22.4583 13 22.2828L20 18.2828C20.3037 18.1074 20.556 17.8552 20.7315 17.5516C20.9071 17.2479 20.9996 16.9035 21 16.5528V8.55276C20.9996 8.20203 20.9071 7.85757 20.7315 7.55392C20.556 7.25027 20.3037 6.99812 20 6.82276L13 2.82276C12.696 2.64722 12.3511 2.55481 12 2.55481C11.6489 2.55481 11.304 2.64722 11 2.82276L4 6.82276C3.69626 6.99812 3.44398 7.25027 3.26846 7.55392C3.09294 7.85757 3.00036 8.20203 3 8.55276V9.55276M15 12.5528C15 14.2096 13.6569 15.5528 12 15.5528C10.3431 15.5528 9 14.2096 9 12.5528C9 10.8959 10.3431 9.55276 12 9.55276C13.6569 9.55276 15 10.8959 15 12.5528Z" stroke="white" stroke-opacity="0.45" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
        Setting
      </app-nav-item>
    </nav>
  </div>
</template>

<style lang="scss">
  .sidebar {
    position: absolute;
    left: 0;
    width: 256px;
    top: 0;
    bottom: 0;
    background-color: #282828;

    &__title {
      font-size: 24px;
      font-weight: 500;
      line-height: 24px;
      text-align: left;
      color: white;

      margin-top: 30px;
      margin-left: 56px;
    }
  }
</style>