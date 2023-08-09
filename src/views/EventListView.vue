<script setup>
import EventService from "@/Services/EventService";
import {onMounted, ref} from "vue";
import EventCard from "@/components/EventCard.vue";

const events = ref(null)

onMounted(() => {
  EventService.getEvents()
      .then(function (response) {
        console.log(response.data)
        events.value = response.data
      })
      .catch(function (error) {
        console.log(error)
      })
})
</script>

<template>
  <h2>Events</h2>
  <div class="events">
    <EventCard v-for="event in events" :key="event.id" :event="event"/>
  </div>
</template>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
