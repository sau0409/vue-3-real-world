<template>
  <div class="events">
    <h1>Events For Good</h1>
    <EventCard v-for="(event, index) in events" :key="index" :event="event"></EventCard>
  </div>
</template>

<script>
import EventCard from '../components/EventCard';
import EventService from '../Services/EventService.js';

export default {
  name: 'EventList',
  components: {
    EventCard
  },
  data() {
    return {
       events: null
    }
  },
  created() {
    EventService.getEvents()
    .then(res=> this.events = res.data)
    .catch(err=> console.lof(err))
  }
}
</script>

<style scoped>
.events{
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}
</style>