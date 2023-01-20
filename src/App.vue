<template>
  <div class="black-bg">
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
    <h4 :style="style">{{ products[0] }}</h4>
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
