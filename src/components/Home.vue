<template>
  <div class="home">
    <Loading v-if="detailsLoading" />
    <div v-if="!detailsLoading" class="home__events">
      <input
        class="search-bar"
        type="text"
        v-model="searchKey"
        placeholder="Search events"
      />
      <div v-if="sortedEvents(eventsData).length <= 0" class="not-found">No matches found</div>
      <div
        v-for="event in sortedEvents(eventsData)"
        :key="event.id"
        class="event"
        @click="goToDetails(event.id)"
      >
        <div class="event__img"></div>
        <div class="event__description">
          <span style="color: #ff6b6b; margin: 8px 0px">{{
            new Date(event.starts).toLocaleString()
          }}</span>
          <h3 style="margin: 8px 0px; color: #424b54">
            {{ event.name }}
          </h3>
          <p
            style="
              padding: 2px;
              margin: 8px 0px;
              font-size: 12px;
              color: #424b54;
            "
          >
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
import Loading from "./Loading.vue";
export default {
  name: "Home",
  props: ["eventsData"],
  components: {
    Loading,
  },
  data() {
    return {
      searchKey: "",
      detailsLoading: false,
    };
  },
  methods: {
    // Submit the selected event ID
    goToDetails(eventId) {
      this.detailsLoading = true;
      this.$emit("goToDetails", eventId);
    },
    // Sorting events
    sortedEvents(events) {
      return events
        .filter((event) =>
          event.name.toLowerCase().includes(this.searchKey.toLowerCase())
        )
        .sort((a, b) => (a.name > b.name ? 1 : -1));
    },
  },
};
</script>

<style>
.home {
  width: 70%;
  height: 98%;
  background-color: #fcfcfc;
  border: 10px solid #f7b538;
  border-radius: 20px;
  border-left: #fcfcfc;
  border-top-left-radius: 0px;
  border-bottom-left-radius: 0px;
  padding: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.home__events {
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 100%;
  overflow: scroll;
  border-left: 2px solid rgba(204, 204, 204, 0.24);
  border-radius: 2px;
  width: 100%;
}
.event {
  cursor: pointer;
  display: flex;
  align-items: center;
  width: 90%;
  box-shadow: 0.5px 4px 3px 0.1px rgba(204, 204, 204, 0.123);
  margin-top: 20px;
  border-radius: 20px;
  font-family: "Josefin Sans", sans-serif;
  padding: 20px;
}
.event:hover {
  transition: ease 0.5s;
  box-shadow: 1px 4px 2px 0.1px rgba(192, 192, 192, 0.233);
}
.event__img {
  min-width: 150px;
  height: 120px;
  border-radius: 20px;
  margin-right: 20px;
  background-color: #f7b538;
}
.event__description {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
}
.search-bar {
  padding-left: 20px;
  width: 50%;
  min-height: 40px;
  max-height: 40px;
  border: none;
  background-color: rgba(192, 192, 192, 0.233);
  color: #424b547e;
  font-family: "Josefin Sans", sans-serif;
  font-size: 16px;
  font-weight: 700;
  border-radius: 20px;
}
.search-bar::-webkit-input-placeholder {
  color: #424b5473;
}
.search-bar:focus {
  border: 2px solid #f7b538;
  outline: none;
  padding-left: 18px;
}
.not-found {
  color: #424b547e;
  font-family: "Josefin Sans", sans-serif;
  font-size: 24px;
  margin-top: 50px;
}
@media screen and (max-width: 768px), screen and (max-height: 600px) {
  .home {
    width: 100%;
    height: unset;
    border: none;
  }
  .home__events {
    border: none;
    margin-top: auto;
  }
}
@media screen and (max-width: 450px) {
  .event {
    flex-direction: column;
  }
  .event__img {
    margin: 0px;
  }
  .event__description {
    text-align: center;
  }
}
</style>
