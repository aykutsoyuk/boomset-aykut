<template>
  <div id="app">
    <div class="main">
      <Loading v-if="mainLoading" />
      <div v-if="!mainLoading" class="main__container">
        <Sidebar :groupsData="groups" @backToHome="backToHome()" />
        <Home
          v-if="!showDetails"
          :eventsData="events"
          @goToDetails="selectedEvent($event)"
        />
        <EventDetails
          v-if="showDetails"
          :eventData="eventData"
          :eventSessions="eventSessions"
          :eventGuests="eventGuests"
          @backToHome="backToHome()"
        />
      </div>
    </div>
  </div>
</template>

<script>
import Sidebar from "./components/Sidebar.vue";
import Home from "./components/Home.vue";
import EventDetails from "./components/EventDetails.vue";
import Loading from "./components/Loading.vue";

export default {
  name: "App",
  components: {
    Sidebar,
    Home,
    EventDetails,
    Loading,
  },
  data() {
    return {
      events: [],
      groups: [],
      eventSessions: null,
      eventData: null,
      eventGuests: null,
      showDetails: false,
      mainLoading: true,
      requestOptions: {
        method: "GET",
        headers: {
          "Content-type": "application/json",
          Authorization: "Token ed56d8f5cbc4f810ff1a7a5ccb7af8e6",
        },
        redirect: "follow",
      },
    };
  },
  methods: {
    selectedEvent(id) {
      // Get selected event sessions
      fetch(`/events/${id}/sessions`, this.requestOptions)
        .then((response) => response.json())
        .then((result) => {
          this.eventSessions = result.results;
          this.showDetails = true;
        })
        .catch((error) => console.log("error", error));
      // Get selected event guests
      fetch(`/events/${id}/guests`, this.requestOptions)
        .then((response) => response.json())
        .then((result) => {
          this.eventGuests = result.count;
        })
        .catch((error) => console.log("error", error));
      // Get selected event data
      fetch(`/events/${id}`, this.requestOptions)
        .then((response) => response.json())
        .then((result) => {
          this.eventData = result;
        })
        .catch((error) => console.log("error", error));
    },
    getEvents(eventsData) {
      this.events = eventsData;
    },
    getGroups(groupsData) {
      this.groups = groupsData;
    },
    backToHome() {
      this.showDetails = false;
    },
  },
  created() {
    // Request to take events data
    fetch("/events", this.requestOptions)
      .then((response) => response.json())
      .then((result) => {
        this.getEvents(result.results);
      })
      .catch((error) => console.log("error", error))
      .finally(() => this.mainLoading = false)
    // Request to take groups data
    fetch("/groups", this.requestOptions)
      .then((response) => response.json())
      .then((result) => {
        this.getGroups(result.results);
      })
      .catch((error) => console.log("error", error));
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0px;
  padding: 0px;
}

#app {
  width: 100vw;
  height: 100vh;
}

.main {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #fcfcfc;
}

.main__container {
  width: 98%;
  height: 98%;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #fcfcfc;
  border-radius: 20px;
}
@media screen and (max-width: 768px), screen and (max-height: 600px) {
  .main__container {
    flex-direction: column;
    padding: 10px 0px;
    justify-content: unset;
  }
}
</style>
