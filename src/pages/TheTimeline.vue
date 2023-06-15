<template>
  <div class="mt-7">
    <ul>
      <TimelineItem
        v-for="timelineItem in timelineItems"
        :key="timelineItem.hour"
        :timeline-item="timelineItem"
      />
    </ul>
  </div>
</template>

<script setup>
import { isTimelineValid } from '../validators'
import TimelineItem from '../components/TimelineItem.vue'

defineProps({
  timelineItems: {
    required: true,
    type: Array,
    validator(timelineItems) {
      return timelineItems.every(isTimelineValid)
    }
  }
})
</script>

<style lang="scss" scoped></style>
