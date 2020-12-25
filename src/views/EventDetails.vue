<template>
  <div class="event-details" v-if="event">
    <h1>{{ event.title }}</h1>
    <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
    <p>{{ event.description }}</p>
  </div>
</template>

<script>
import EventService from "../Services/EventService.js";

export default {
  name: "EventDetails",
  props: {
      id: null
  },
  data() {
    return {
      event: null,
    };
  },
  created() {
    EventService.getEvent(this.id)
      .then((res) => (this.event = res.data))
      .catch((err) => console.lof(err));
  },
};
</script>

<style>
.event-link {
  color: #2c3e50;
  text-decoration: none;
}
</style>
