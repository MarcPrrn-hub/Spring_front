<template>
  <div class="room border border-secondary rounded p-2 mb-2" :class="{expanded: isExpanded}">
    <div class="top-row d-flex" @click="toggleExpand">
      <div class="room-name fw-bold pe-3">{{room.name}}</div>
      <div>  Floor :  </div>
      <div class="room-floor ms-2">{{room.floor}}</div>
      <div class="ms-2">  current temperature :  </div>
      <div class="room-current-temp ms-2">{{room.currentTemperature}}</div>
       <div class="ms-2">  target temperature :  </div>
      <div class="room-target-temp ms-2">{{room.targetTemperature}}</div>
      <div class="expand-button ms-auto">
        {{ isExpanded ? '&#9660;' : '&#9658;' }}
      </div>
    </div>
    <template v-if="isExpanded">
      <hr/>
      <div class="details d-flex">
        <button type="button" class="btn btn-danger"  @click="deleteroom">Delete room</button>
      </div>
    </template>    
  </div>
</template>

<script>
import axios from 'axios';
import {API_HOST} from '../config';

export default {
  name: 'roomsListItem',
  props: ['room'],
  data: function() {
    return {
      isExpanded: false
    }
  },
  methods: {
    toggleExpand() {
      this.isExpanded = !this.isExpanded;
    },
    async deleteroom() {
      let response = await axios.delete(`${API_HOST}/api/rooms/${this.room.id}`);
      let updatedroom = response.data;
      this.$emit('room-updated', updatedroom);
    }
  }
}
</script>

<style lang="scss" scoped>

.room {
  .top-row {
    cursor: pointer;
  }
}
</style>
