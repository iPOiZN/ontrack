<template>
  <div class="flex gap-2">
    <BaseButton :type="BUTTON_TYPE_NEUTRAL"
                @click="select(null)">
      <XMarkIcon class="h-8" />
    </BaseButton>
    <select class="w-full truncate rounded bg-gray-100 px-2 py-1 text-2xl focus:outline-purple-400"
            @change="select($event.target.value)">
      <option :selected="isNotSelected"
              disabled
              value="">
        {{ placeholder }}
      </option>
      <option v-for="{ value, label } in options"
              :key="value"
              :value="value"
              :selected="value === selected">
        {{ label }}
      </option>
    </select>
  </div>
</template>

<script setup>
import { computed } from 'vue'
import { XMarkIcon } from '@heroicons/vue/24/outline'
import { BUTTON_TYPE_NEUTRAL } from '../constants'
import { normalizeSelectValue } from '@/functions'
import { validateSelectOptions, isUndefinedOrNull, isSelectValueValid  } from '@/validators'
import BaseButton from './BaseButton.vue'

// defineProps(['selected', 'options', 'placeholder'])
const props = defineProps({
  selected: [String, Number],
  placeholder: {
    required: true,
    type: String
  },
  options: {
    required: true,
    type: Array,
    validator: validateSelectOptions
  }
})

const emit = defineEmits({
  select: isSelectValueValid
})

const isNotSelected = computed(() => {
  return isUndefinedOrNull(props.selected)
})

function select(value){
  emit('select', normalizeSelectValue(value))
}
</script>

<style lang="scss" scoped></style>
