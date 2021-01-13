<template>
    <div>

      <button v-for="tab in tabs" :key="tab" @click="selected = tab;">
            {{ tab }}
          </button>
      <!-- <button class="nav-link me-2" href="#" @click="change_tab_window" >Windows</button>
      <button type="button" class="nav-link" href="#"  @click="change_tab_room">Rooms</button>
      These two lines were not used for this version-->

        <component :is="selected" class="tab"></component>
    </div>
</template>

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

