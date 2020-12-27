<template>
  <div class="details">
    <div class="event-data">
      <p>{{ eventGuests }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "EventDetails",
  props: ["eventData", "eventSessions", "eventGuests"],
  methods: {},
};
</script>

<style>
.details {
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
.event-data {
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 100%;
  overflow: scroll;
  border-left: 2px solid rgba(204, 204, 204, 0.24);
  border-radius: 2px;
}
</style>
