<template>
  <div class="black-bg" v-if="showModal == true">
    <div class="white-bg">
      <h4>상세페이지임</h4>
      <p>상세페이지 내용임</p>
    </div>
  </div>

  <div class="menu">
    <a v-for="(a, i) in menus" :key="i">{{ menus[i] }}</a>
  </div>

  <div>
    <img src="/room0.jpg" class="image" />
    <h4 :style="style" @click="showModal = !showModal">{{ products[0] }}</h4>
    <p>50 만원</p>
    <button
      @click="
        () => {
          increase(0);
        }
      "
    >
      허위매물신고</button
    ><span>신고 수 : {{ reports[0] }}</span>
  </div>
  <div>
    <img src="/room1.jpg" class="image" />
    <h4 :style="style">{{ products[1] }}</h4>
    <p>60 만원</p>
    <button
      @click="
        () => {
          increase(1);
        }
      "
    >
      허위매물신고</button
    ><span>신고 수 : {{ reports[1] }}</span>
  </div>
  <div>
    <img src="/room2.jpg" class="image" />
    <h4 :style="style">{{ products[2] }}</h4>
    <p>70 만원</p>
    <button
      @click="
        () => {
          increase(2);
        }
      "
    >
      허위매물신고</button
    ><span>신고 수 : {{ reports[2] }}</span>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      showModal: false,
      menus: ["Home", "Products", "About"],
      products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
      prices: [50, 60, 70],
      reports: [0, 0, 0],
    };
  },
  methods: {
    increase(i) {
      this.reports[i]++;
    },
  },
  components: {},
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
