<script setup>
import BInput from "@/components/base/BInput.vue";
import {computed, ref, watchEffect} from "vue";
import BSelect from "@/components/base/BSelect.vue";
import BButton from "@/components/base/BButton.vue";
import CarCard from "@/components/CarCard.vue";
import {useFetch} from "@vueuse/core";

const search = ref("")
const itemPerPage = ref(18)
const itemsPerPage = ref([
  {id: 1, value: 9},
  {id: 2, value: 18},
  {id: 3, value: 27}
])

const currentPage = ref(1)

const fetchCars = async () => {
  const url = `https://api.caiman-app.de/api/cars-test?per_page=${itemPerPage.value}&page=${currentPage.value}&search=${search.value}`;
  const {isFetching, error, data} = await useFetch(url);

  try {
    const json = JSON.parse(data.value)
    cars.value = json.data
    total.value = json.meta.total
    totalPages.value = json.meta.last_page
  }catch (e) {

  }

  return {isFetching, error, data};
};

fetchCars();
const cars = ref([])
const total = ref(0)
const totalPages = ref(0)

const goTo = (page) => {
  if (page < 1 || page > totalPages.value) return
  currentPage.value = page

}

watchEffect(() => {
  fetchCars()
});

</script>

<template>
  <div class="toolbar">
    <b-input search-icon placeholder="Search VIN" @search="log" class="toolbar__search" v-model="search"/>
    <div class="d-flex align-center ml-32">
      <span>Select vehicles per page:</span>
      <b-select :items="itemsPerPage" v-model="itemPerPage" class="ml-16" wrap-classes="toolbar__select">
        <template v-slot:selected="{item}">
          <div class="toolbar__select__item">
            {{ item.value }}
          </div>
        </template>
      </b-select>
    </div>

    <b-button class="d-flex align-center ml-270 toolbar__add">
      <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path fill-rule="evenodd" clip-rule="evenodd" d="M12 4C12.5523 4 13 4.44772 13 5V19C13 19.5523 12.5523 20 12 20C11.4477 20 11 19.5523 11 19V5C11 4.44772 11.4477 4 12 4Z" fill="white"/>
        <path fill-rule="evenodd" clip-rule="evenodd" d="M4 12C4 11.4477 4.44772 11 5 11H19C19.5523 11 20 11.4477 20 12C20 12.5523 19.5523 13 19 13H5C4.44772 13 4 12.5523 4 12Z" fill="white"/>
      </svg>
      Add Vechicle
    </b-button>
  </div>
  <div class="car-grid">
    <car-card
        v-for="(car, index) in cars"
        :key="index"
        :car="car"
    />
  </div>
  <div class="footer mt-32">
    <span class="info">Showing {{cars.length}} out of {{ total }}</span>
    <div class="pagination">
      <div class="btn" @click="goTo(currentPage - 1)">
        <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M14 16L10 12L14 8" stroke="#293148" stroke-opacity="0.45" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </div>
      <div class="block">
        <div class="page page--curr">{{ currentPage }}</div>
        <div>of</div>
        <div class="page page--total">{{ totalPages }}</div>
      </div>
      <div class="btn" @click="goTo(currentPage + 1)">
        <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M10 16L14 12L10 8" stroke="#293148" stroke-opacity="0.45" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.car-grid {
  margin-left: 30px;
  margin-right: 32px;
  margin-top: 32px;
  gap: 30px;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
}
.toolbar {
  display: flex;
  padding-left: 30px;
  padding-top: 36px;

  * {
    letter-spacing: 0;
  }

  &__search {
    flex-basis: 354px;
  }

  &__select {
    position: relative;
    height: 42px;
    border: 1px solid #E4E4E4;
    border-radius: 8px;
    padding: 9px 16px;

    &__item {
      margin-right: 14px;
    }
  }

  &__add {
    display: flex;
    gap: 16px;
    border-radius: 10px;
    flex-basis: 180px;
    padding-left: 18px;
  }
}
.footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-left: 30px;
  padding-right: 24px;

  .info {
    letter-spacing: 0 !important;
    font-size: 16px;
    font-weight: 400;
    line-height: 22px;
    text-align: left;
    color: #293148CC;
  }
}
.pagination {
  display: flex;
  gap: 13px;
  margin-right: 4px;
  margin-bottom: 30px;

  .block {
    width: 112px;
    display: flex;
    justify-content: space-between;
    align-items: center;

    font-size: 13px;
    font-weight: 400;
    line-height: 24px;
    text-align: center;
  }

  .page {
    width: 32px;
    height: 32px;
    display: flex;
    justify-content: center;
    align-items: center;
    border: 1px solid #E4E4E4;
    border-radius: 6px;

    font-size: 15px;
    font-weight: 400;
    line-height: 22px;
    text-align: center;

    &--curr {
      color: #293148CC;
    }
    &--total {
      color: #29314873;
    }
  }

  .btn {
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;

    transition: all 0.3s ease-in-out;

    &:hover {
      background-color: #E4E4E4;
      border-radius: 6px;
    }
  }
}
</style>

