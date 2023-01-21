<template>
  <div class="black-bg" v-if="modalNumber > -1">
    <div class="white-bg">
      <h4>{{ rooms[modalNumber].title }}</h4>
      <p>{{ rooms[modalNumber].content }}</p>
      <button @click="modalNumber = -1">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="(a, i) in menus" :key="i">{{ menus[i] }}</a>
  </div>

  <DiscountPage />

  <div v-for="(room, i) in rooms" :key="room">
    <img :src="room.image" class="image" />
    <h4
      @click="
        () => {
          modalNumber = i;
        }
      "
    >
      {{ room.title }}
    </h4>
    <p>{{ room.price + " 원" }}</p>
  </div>
</template>

<script>
import list from "./assets/data.js";
import DiscountPage from "./DiscountPage.vue";

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
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  margin: 10px;
  padding: 25px;
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
.image {
  width: 30rem;
  height: 15rem;
}
</style>
