<template>
  <div class="home">
    <div class="events">
      <div
        v-for="event in sortedEvents(eventsData)"
        :key="event.id"
        class="event-container"
        @click="goToDetails(event.id)"
      >
        <div class="event-image"></div>
        <div class="event-info">
          <span style="color: #ff6b6b; margin: 8px 0px">{{
            new Date(event.starts).toLocaleString()
          }}</span>
          <h3 style="margin: 8px 0px">
            {{ event.name }}
          </h3>
          <p style="padding: 2px; margin: 8px 0px; font-size: 12px">
            Lorem, ipsum dolor sit amet consectetur adipisicing elit.
            Reprehenderit suscipit, sint hic quaerat sunt amet sit vero
            inventore aliquam error!
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  props: ["eventsData"],
  methods: {
    goToDetails(eventId) {
        this.$emit("goToDetails", eventId)
    },
    sortedEvents(events) {
      return events.sort((a, b) => (a.name > b.name ? 1 : -1));
    },
  },
};
</script>

<style>
.home {
  width: 70%;
  height: 98%;
  background-color: #fcfcfc;
  border: 10px solid #fff3df;
  border-radius: 20px;
  border-left: #fcfcfc;
  border-top-left-radius: 0px;
  border-bottom-left-radius: 0px;
  padding: 20px;
}
.events {
  display: flex;
  flex-direction: column;
}
.event-container {
  display: flex;
  align-items: center;
  width: 90%;
  box-shadow: 0.5px 4px 5px 0.1px rgba(204, 204, 204, 0.432);
  margin-top: 20px;
  border-radius: 20px;
  font-family: "Josefin Sans", sans-serif;
}
.event-image {
  width: 150px;
  height: 120px;
  border-radius: 20px;
  margin: 20px;
  background-color: #f7b538;
}
.event-info {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
}
</style>
