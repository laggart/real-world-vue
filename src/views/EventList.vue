
<template>
  <main> 
    <div class="events">
      <h1>Events For Good</h1> 
        <EventCard v-for="event in events" :key="event.id" :event="event" />  
    </div> 
  </main>
</template>

<script>
// @ is an alias to /src
  import EventCard from '../components/EventCard.vue'
  import EventService from '../services/EventService.js'

  export default {
    name: 'EventList',
    components: {
      EventCard // register it as a child component
    },
    data() {
      return {
        events: null
      }
    },
    created() {
      // get events from EventService when component is created (axios)
      EventService.getEvents()
        .then(response => {
          this.events = response.data
        })
        .catch(error => {
          console.log(error)
        })
    }
  }
</script>
<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}

</style>