<template>
  <div class="menu">
    <a v-for="(a, i) in menus" :key="i">{{ menus[i] }}</a>
  </div>
  <DiscountPage />
  <ModalComp
    @closeButton="modalNumber = -1"
    :rooms="rooms"
    :index="modalNumber"
  />
  <div v-for="room in rooms" :key="room.id">
    <RoomCell @openModal="modalNumber = $event" :room="room" />
  </div>
</template>

<script>
import list from "./assets/data.js";
import DiscountPage from "./DiscountPage.vue";
import ModalComp from "./ModalComp.vue";
import RoomCell from "./Room.vue";

export default {
  name: "App",
  data() {
    return {
      modalNumber: -1,
      rooms: list,
      menus: ["Home", "Products", "About"],
    };
  },
  methods: {
    increase(i) {
      this.reports[i]++;
    },
  },
  components: {
    DiscountPage: DiscountPage,
    ModalComp: ModalComp,
    RoomCell: RoomCell,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
body {
  margin: 0;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}
</style>
