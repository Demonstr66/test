<script setup>

import BSelect from "@/components/base/BSelect.vue";
import AppLangIcon from "@/components/layout/AppLangIcon.vue";
import {ref} from "vue";

const langs = ref([
  {id: 1, name: "En", value: "En-en"},
  {id: 2, name: "Ru", value: "Ru-ru"},
])

const selectedLang = ref("En-en")
</script>

<template>
  <b-select :items="langs" v-model="selectedLang">
    <template v-slot:selected="{item}">
      <div class="item">
        <app-lang-icon :lang="item.value" />
        <span class="ml-14">{{item.name}}</span>
      </div>
    </template>
    <template v-slot:option="{item}">
      <div class="item">
        <app-lang-icon :lang="item.value" />
        <span class="ml-14">{{item.name}}</span>
      </div>
    </template>
  </b-select>
</template>

<style lang="scss">
.item {
  display: flex;
  align-items: center;
  font-size: 15px;
  font-weight: 500;
  line-height: 22px;
}
</style>