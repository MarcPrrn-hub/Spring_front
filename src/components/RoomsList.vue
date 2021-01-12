<template>
  <div class="rooms-list pt-3">
    <rooms-list-item 
      v-for="room in rooms"
      :room="room"
      :key="room.id"  
    >
    </rooms-list-item>
  </div>
</template>


<script>
import axios from 'axios';
import {API_HOST} from '../config';
import roomsListItem from './RoomsListItem';

export default {
  components: {
    roomsListItem
  },
  name: 'roomsList',
  data: function() {
    return {
      /* Initialize rooms with an empty array, while waiting for actual data to be retrieved from the API */
      rooms: []
    }
  },
  created: async function() {
    let response = await axios.get(`${API_HOST}/api/rooms`);
    let rooms = response.data;
    this.rooms = rooms;
  },
  methods: {
    updateroom(newroom) {
      /* Find the place of room object with the same Id in the array, and replace it */
      let index = this.rooms.findIndex(room => room.id === newroom.id);
      this.rooms.splice(index, 1, newroom);
    }
  }
}
</script>
