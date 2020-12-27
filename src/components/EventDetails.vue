<template>
  <div class="home">
    <div class="events">
        <!-- <p v-for="event in eventsData" :key="event.id">{{ event.name }}</p> -->
        <p>EVENT Details</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Home',
  props: []
}
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
  }
  .events {
   
  }

</style>
