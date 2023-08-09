<script setup>
defineProps({
  event: {
    type: Object,
    required: true,
  }
})
</script>

<template>
  <RouterLink :to="{ name: 'event-details', params: {id: event.id}}">
    <div class="card mt-2">
      <div class="card-header">
        {{ event.title }}
      </div>
      <div class="card-body">
        <span>{{ event.description }}</span>
      </div>
    </div>
  </RouterLink>
</template>
