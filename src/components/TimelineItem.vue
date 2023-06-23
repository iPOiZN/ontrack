<template>
  <li class="relative flex flex-col gap-2 border-t border-gray-200 px-4 py-10">
    <TimelineHour :hour="timelineItem.hour" />
    <BaseSelect
      placeholder="Rest"
      :selected="selectedActivityId"
      :options="activitySelectOptions"
      @select="selectedActivityId = $event"
    />
  </li>
</template>

<script setup>
import { ref } from 'vue'
import { isTimelineItemValid, validateSelectOptions } from '../validators'
import BaseSelect from '@/components/BaseSelect.vue'
import TimelineHour from '@/components/TimelineHour.vue'

defineProps({
  timelineItem: {
    required: true,
    type: Object,
    validator: isTimelineItemValid
  },
  activitySelectOptions: {
    required: true,
    type: Array,
    validator: validateSelectOptions
  }
})

const selectedActivityId = ref(0)
</script>

<style lang="scss" scoped></style>
