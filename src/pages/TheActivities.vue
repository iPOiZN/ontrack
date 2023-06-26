<template>
  <div class="flex grow flex-col">
    <ul v-if="activities.length > 0" class="grow divide-y">
      <ActivityItem v-for="activity in activities" :key="activity.id" :activity="activity"
        @delete="emit('deleteActivity', activity)" />
    </ul>
    <TheActivitiesEmptyState v-else />
    <TheActivityForm @submit="emit('createActivity', $event)" />
  </div>
</template>

<script setup>
import ActivityItem from '@/components/ActivityItem.vue'
import TheActivitiesEmptyState from '@/components/TheActivitiesEmptyState.vue'
import { isActivityValid, validateActivities } from '../validators'
import TheActivityForm from '@/components/TheActivityForm.vue'

defineProps({
  activities: {
    required: true,
    type: Array,
    validator: validateActivities
  }
})

const emit = defineEmits({
  createActivity: isActivityValid,
  deleteActivity: isActivityValid
})
</script>

<style lang="scss" scoped></style>
