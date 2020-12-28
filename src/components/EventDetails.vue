<template>
  <div class="container__details">
    <div class="event__header">
      <span>{{ eventData.name }}</span>
    </div>
    <div class="event__data">
      <div class="event__details">
        <div class="event__image"></div>
        <div class="event__dates" style="color: #424b54">
          Start:
          <span style="color: #ff6b6b">{{
            new Date(eventData.starts).toLocaleString()
          }}</span>
          <br />
          End:
          <span style="color: #ff6b6b">{{
            new Date(eventData.ends).toLocaleString()
          }}</span>
        </div>
        <div class="event__info">
          <p style="color: #424b54">
            Lorem ipsum dolor sit amet consectetur, adipisicing elit. Modi
            laudantium maxime reprehenderit molestiae voluptatum deserunt est
            officia dolor cupiditate eos repellat temporibus labore soluta a
            earum cum, et porro architecto dignissimos eaque qui distinctio
            commodi minima hic?
            <br />
            <br />
            Nemo sed harum sequi.
            <br />
            <br />
            Dolorum suscipit deserunt beatae inventore hic tenetur quod nemo?
          </p>
        </div>
        <div style="color: #424b54; font-size: 24px">
          {{ eventGuests }} Guests
        </div>
      </div>
      <div class="container__sessions">
        <h3 style="color: #424b54">Sessions</h3>
        <div
          v-for="session in sortedSessions(eventSessions)"
          :key="session.id"
          class="session"
        >
          <span style="color: #ff6b6b">{{
            new Date(session.starts).toLocaleString()
          }}</span>
          <h4 style="margin: 2px 0px 25px 0px; color: #424b54">
            {{ session.name }}
          </h4>
        </div>
        <button class="back-button" @click="backToHome()">
          <span
            style="
              color: #fcfcfc;
              font-family: 'Josefin Sans', sans-serif;
              font-size: 20px;
              margin-top: 4px;
            "
            >Go back</span
          >
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "EventDetails",
  props: ["eventData", "eventSessions", "eventGuests"],
  methods: {
    backToHome() {
      this.$emit("backToHome", true);
    },
    // Sorting sessions
    sortedSessions(sessions) {
      return sessions.sort((a, b) => (a.starts > b.starts ? 1 : -1));
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Josefin+Sans:wght@300;400;600;700&display=swap");

.container__details {
  width: 70%;
  height: 98%;
  background-color: #fcfcfc;
  border: 10px solid #f7b538;
  border-radius: 20px;
  border-left: #fcfcfc;
  border-top-left-radius: 0px;
  border-bottom-left-radius: 0px;
  padding: 20px;
}
.event__data {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  height: 97%;
  overflow: scroll;
  border-left: 2px solid rgba(204, 204, 204, 0.24);
  border-radius: 2px;
}
.event__details {
  padding: 20px;
  width: 50%;
  height: 100%;
  background-color: #fcfcfc;
  font-family: "Josefin Sans", sans-serif;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
}
.container__sessions {
  padding: 20px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  height: 100%;
  width: 50%;
  background-color: #fcfcfc;
  font-family: "Josefin Sans", sans-serif;
  border-left: 2px solid rgba(204, 204, 204, 0.24);
  border-radius: 2px;
}
.session {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
.back-button {
  cursor: pointer;
  width: 100px;
  height: 30px;
  border-radius: 20px;
  background-color: #f7b538;
  text-decoration: none;
  display: flex;
  justify-content: center;
  align-items: center;
  border: none;
  margin-top: 60px;
}
.event__image {
  width: 100%;
  margin-bottom: 20px;
  height: 120px;
  border-radius: 20px;
  background-color: #f7b538;
}
.event__header {
  text-align: center;
  font-size: 24px;
  font-family: "Josefin Sans", sans-serif;
  line-height: 30px;
  font-weight: 700;
  color: #424b54;
}
@media screen and (max-width: 768px), screen and (max-height: 600px) {
  .container__sessions {
    justify-content: space-between;
  }
  .container__details {
    width: 100%;
    height: unset;
    border: none;
  }
  .event__data {
    border: none;
  }
}
@media screen and (max-width: 550px) {
  .event__data {
    border: none;
    flex-direction: column;
  }
  .event__details {
    width: unset;
    padding-bottom: 10px;
  }
  .container__sessions {
    width: 100%;
    border-left: unset;
    border-top: 2px solid rgba(204, 204, 204, 0.24);
    margin-top: 20px;
  }
  .back-button {
    margin-top: 20px;
  }
}
</style>
