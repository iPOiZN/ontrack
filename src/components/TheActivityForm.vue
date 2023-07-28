<template>
  <form @submit.prevent="submit"
        class="sticky bottom-[57px] flex gap-2 border-t bg-white p-4"
        action="#">
    <input type="text"
           v-model="name"
           class="w-full rounded border px-4 text-xl focus:outline-[#6B62FF]"
           placeholder="Activity name" />
    <BaseButton :disabled="name.trim() === ''">
      <PlusIcon class="h-8" />
    </BaseButton>
  </form>
</template>

<script setup>
import { nextTick, ref } from 'vue'
import { isActivityValid } from '../validators'
import BaseButton from './BaseButton.vue'
import { PlusIcon } from '@heroicons/vue/24/outline'
import { generateId } from "@/functions"

const emit = defineEmits({
  submit: isActivityValid
})

const name = ref('')
async function submit() {
  emit('submit', {
    id: generateId(),
    name: name.value,
    secondsToComplete: 0
  })

  name.value = ''

  await nextTick()

  window.scrollTo(0, document.body.scrollHeight)
}
</script>

<style lang="scss" scoped></style>
