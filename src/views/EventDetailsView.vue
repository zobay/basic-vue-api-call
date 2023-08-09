<script setup>
import {onMounted, ref} from "vue";
import EventService from "@/Services/EventService";

const props = defineProps({
  id: {
    required: true,
  }
})

const event = ref(null)

onMounted(() => {
  EventService.getEvent(props.id)
      .then((response) => {
        event.value = response.data
      })
      .catch((error) => {

      })
})

</script>

<template>
  <div v-if="event" class="card">
    <div class="card-header">
      {{ event.title }}
    </div>
    <span class="card-body">
      {{ event.time }} on {{ event.date }}
    </span>
  </div>
</template>
