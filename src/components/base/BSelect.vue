<script setup>
import {computed, ref, watchEffect} from 'vue';
import { onClickOutside } from '@vueuse/core';

const props = defineProps({
  items: {
    type: Array,
    required: true
  },
  id: {
    type: String,
    default: "id"
  },
  value: {
    type: String,
    default: "value"
  },
  modelValue: {
    type: String,
    default: ''
  },
  wrapClasses: {
    type: String,
    default: ''
  },
})

const emits = defineEmits(['update:modelValue']);

const selectedValue = ref(props.modelValue);
const isOpen = ref(false);
const selectElement = ref(null);

watchEffect(() => {
  selectedValue.value = props.modelValue;
});

const open = () => isOpen.value = true
const close = () => isOpen.value = false

const selectedOption = computed(() => {
  return props.items.find(item => item[props.value] === selectedValue.value)
})

onClickOutside(selectElement, () => {
  close()
});

const updateSelectedOption = (option) => {
  selectedValue.value = option[props.value];
  emits('update:modelValue', selectedValue.value);
  close()
};

defineExpose({ updateSelectedOption });
</script>


<template>

  <div ref="selectElement" class="b-select" :class="{'b-select--opened': isOpen}">
    <div class="selected-option d-flex align-center" @click="open" :class="[wrapClasses]">
      <slot name="selected" :item="selectedOption">
        {{ selectedOption[value] }}
      </slot>
      <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg" class="chevron ml-4">
        <path d="M16 10L12 14L8 10" stroke="#293148" stroke-opacity="0.6" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
      </svg>
    </div>
    <transition name="slide">
      <ul v-if="isOpen" class="options-container">
        <li
            v-for="option in items"
            :key="option[key]"
            @click="updateSelectedOption(option)"
            class="option"
        >
          <slot name="option" :item="option">
            {{ option[value] }}
          </slot>
        </li>
      </ul>
    </transition>
  </div>
</template>

<style scoped lang="scss">
.b-select {
  position: relative;
  cursor: pointer;

  .chevron {
    transition: transform .4s ease-in-out;
  }

  &--opened {
    & .chevron {
      transform: rotateX(180deg);
    }
  }
}

.options-container {
  position: absolute;
  z-index: 30;
  width: 100%;
  border: 1px solid #E4E4E4;
  border-radius: 8px;
  background-color: #fff;
  max-height: 200px;
  overflow-y: auto;

  transform-origin: top;
  transition: transform .4s ease-in-out;
}

.option {
  position: relative;
  padding: 10px;
  cursor: pointer;

  &:hover::after {
    content: "";
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    background-color: rgba(0, 0, 0, 0.12);
  }
}

.slide-enter,
.slide-leave-to {
  transform: scaleY(0);
}

</style>
