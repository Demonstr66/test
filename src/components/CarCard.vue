<script setup>

import moment from 'moment';
import BBadge from "@/components/base/BBadge.vue";
import {computed, ref} from "vue";

const props = defineProps({
  car: {
    type: Object,
    required: true
  }
})

const photo = computed(() => {
  return require('@/assets/car.png')
})


const formattedDate = computed(() => {
  return moment.utc(props.car.created_at, 'X').fromNow()
})

const count = ref(Math.ceil((Math.random() * 30 + 1)))
const max = ref(30)
const active = ref(count === max)

</script>

<template>
  <div class="car">
    <div class="car__content">
      <div class="car__tools">
        <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M19 13C19.5523 13 20 12.5523 20 12C20 11.4477 19.5523 11 19 11C18.4477 11 18 11.4477 18 12C18 12.5523 18.4477 13 19 13Z" stroke="#293148" stroke-opacity="0.6" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          <path d="M12 13C12.5523 13 13 12.5523 13 12C13 11.4477 12.5523 11 12 11C11.4477 11 11 11.4477 11 12C11 12.5523 11.4477 13 12 13Z" stroke="#293148" stroke-opacity="0.6" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          <path d="M5 13C5.55228 13 6 12.5523 6 12C6 11.4477 5.55228 11 5 11C4.44772 11 4 11.4477 4 12C4 12.5523 4.44772 13 5 13Z" stroke="#293148" stroke-opacity="0.6" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </div>
      <div class="car__image">
        <img :src="photo" alt="" />
      </div>
      <div class="mt-9">
        <h6 class="car__title">{{car.vehicle_name || "-"}}</h6>
        <div class="car__subtitle mt-12">{{car.vin}}</div>
      </div>
    </div>
    <div class="d-flex flex-column">
      <div class="car__divider"></div>
      <div class="car__footer mt-17">
        <b-badge class="car__badge" v-if="!active">{{ count }}/{{ max }}</b-badge>
        <b-badge class="car__badge--active" v-else>
          <svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M13.3333 4L5.99999 11.3333L2.66666 8" stroke="#7FC75E" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
          {{ count }}/{{ max }}
        </b-badge>
        <span class="car__status">{{ formattedDate }}</span>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.car {
  position: relative;
  min-height: 335px;
  border-radius: 10px;
  background: #F3F6F8;
  padding: 24px;
  padding-top: 30px;
  padding-bottom: 17px;

  display: flex;
  flex-direction: column;
  justify-content: space-between;
  gap: 17px;

  &__divider {
    border-bottom: 1px solid #E4E4E4;
  }

  &__content {
    flex-grow: 1;
  }

  &__tools {
    position: absolute;
    right: 20px;
    top: 20px;

    cursor: pointer;
  }
  &__image {
    width: 100%;

    padding: 10px 23px;

    & > img {
      width: 100%;
    }
  }
  &__title {
    display: block;
    font-size: 20px;
    font-weight: 700;
    line-height: 22px;
    text-align: left;
    color: #293148;
    letter-spacing: -0.01em;
  }
  &__subtitle {
    font-size: 15px;
    font-weight: 500;
    line-height: 20px;
    letter-spacing: 0.3px;
    text-align: left;
    color: #29314899;
  }

  &__status {
    font-size: 15px;
    font-weight: 500;
    line-height: 16px;
    text-align: right;
    letter-spacing: 0px;
    color: #29314899;
  }

  &__badge {
    background-color: #EDEDED !important;
    color: #293148CC !important;
    letter-spacing: 0;

    &--active {
      display: flex;
      gap: 6px;
      align-items: center;
      background-color: #E4F5DD !important;
      color: #7FC75E !important;
    }
  }

  &__footer {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding-top: 1px;
  }
}
</style>