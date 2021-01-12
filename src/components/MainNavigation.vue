<template>
  <ul class="nav nav-tabs">
    <li class="nav-item">
      <button class="nav-link me-2" href="#" @click="change_tab_window" >Windows</button>
    </li>
    <li class="nav-item">
      <button type="button" class="nav-link" href="#"  @click="change_tab_room">Rooms</button>
    </li>
  </ul>
</template>

//changer les fonctions pour que tab_window et tab_room puisse etre récup dans App pour l'affichage conditionel
<script>
export default {
  name: 'MainNavigation',
  props: {
    tab_window: Boolean,
    tab_room: Boolean,
  },
  methods: {
    change_tab_room() {
      this.tab_window = false;
      this.tab_room = true;
      console.log(this.tab_window)
      console.log(this.tab_room)

    },
    change_tab_window() {
      this.tab_window = true;
      this.tab_room = false;
      console.log(this.tab_window)
      console.log(this.tab_room)
    }
  }
}
</script>
