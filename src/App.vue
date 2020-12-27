<template>
  <div id="app">
    <div class="main-container">
      <div class="container">
        <Sidebar :groupsData="groups" />
        <Home :eventsData="events" @goToDetails="selectedEvent($event)"/>
        <!-- <EventDetails /> -->
      </div>
    </div>
  </div>
</template>

<script>
import Sidebar from "./components/Sidebar.vue";
import Home from "./components/Home.vue";
// import EventDetails from "./components/EventDetails.vue";

export default {
  name: "App",
  components: {
    Sidebar,
    Home,
    // EventDetails,
  },
  data() {
    return {
      events: [],
      groups: [],
    };
  },
  methods: {
    selectedEvent(id) {
      console.log(id)
    },
    getEvents(eventsData) {
      this.events = eventsData;
    },
    getGroups(groupsData) {
      this.groups = groupsData;
    },
  },
  created() {
    var requestOptions = {
      method: "GET",
      headers: {
        "Content-type": "application/json",
        Authorization: "Token ed56d8f5cbc4f810ff1a7a5ccb7af8e6",
      },
      redirect: "follow",
    };
    // Request to take events data
    fetch("/events", requestOptions)
      .then((response) => response.json())
      .then((result) => {
        this.getEvents(result.results);
      })
      .catch((error) => console.log("error", error));
    // Request to take groups data
    fetch("/groups", requestOptions)
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

.main-container {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #fae7c5;
}

.container {
  width: 98%;
  height: 98%;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #fcfcfc;
  border-radius: 20px;
}
</style>
