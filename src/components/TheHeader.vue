<template>
  <header class="sticky top-0 z-20 flex items-center justify-between border-b bg-white p-3">
    <TheLogo @click="emit('navigate', PAGE_TIMELINE)" />
    <TheHeaderProgress @click="emit('navigate', PAGE_PROGRESS)" />
  </header>
</template>

<script setup>
import { PAGE_TIMELINE, PAGE_PROGRESS } from '../constants'
import TheLogo from '@/components/TheLogo.vue'
import { isPageValid } from '../validators'
import TheHeaderProgress from '@/components/TheHeaderProgress.vue'

const emit = defineEmits({
  navigate: isPageValid
})
</script>

<style lang="scss" scoped></style>
