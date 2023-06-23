<template>
  <button
    :class="`${typeClasses[type]} rounded p-3 disabled:cursor-not-allowed disabled:opacity-50`"
  >
    <slot></slot>
  </button>
</template>
<script>
import { BUTTON_TYPE_DANGER, BUTTON_TYPE_NEUTRAL } from '../constants'
import { isButtonTypeValid } from '../validators'
const typeClasses = {
  [BUTTON_TYPE_DANGER]: 'bg-red-500 enabled:hover:bg-red-600 text-white',
  [BUTTON_TYPE_NEUTRAL]: 'bg-gray-100 enabled:hover:bg-gray-200'
}
</script>
<script setup>
defineProps({
  type: {
    default: 'neutral',
    type: String,
    validator: isButtonTypeValid
  }
})
</script>
