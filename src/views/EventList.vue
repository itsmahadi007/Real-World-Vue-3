<template>
  <div class="events">
    <h4>Events For Good</h4>
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
// @ is an alias to /src
import EventCard from "@/components/EventCard.vue";
import axios from "axios";

export default {
  name: "EventList",
  components: {
    EventCard
  },
  data() {
    return {
      events: null
    };
  },
  created() {
    axios.get("http://testing.easysell.info/userac/")
      .then(response => {
        console.log("events:", response.data);
      })
      .catch(error => {
        console.log(error);
      });
  }
};
</script>

<style>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>