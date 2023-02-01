<template>
  <div class="header">
    <ul class="header-button-left" @click="tabState = 0">
      <li>Cancel</li>
    </ul>
    <ul class="header-button-right">
      <li @click="tabState++" v-if="tabState == 1">Next</li>
      <li v-if="step == 2" @click="publish()">Publish</li>
    </ul>
    <img src="./assets/logo.png" class="logo" />
  </div>

  <ContentContainer :posts="posts" :tabState="tabState" :imageUrl="imageUrl" />
  <button @click="loadContent">더 불러오기</button>

  <div class="footer">
    <ul class="footer-button-plus">
      <input
        @change="handleUpload"
        accept="image/*"
        type="file"
        id="file"
        class="inputfile"
      />
      <label for="file" class="input-plus">+</label>
    </ul>
  </div>
</template>

<script>
import ContentContainer from "./components/ContentContainer.vue";
import PostData from "./assets/data.json";
import axios from "axios";

export default {
  name: "App",
  data() {
    return {
      tabState: 0,
      imageUrl: "",
      posts: PostData,
    };
  },
  components: {
    ContentContainer: ContentContainer,
  },
  methods: {
    handleUpload(e) {
      let files = e.target.files;
      let url = URL.createObjectURL(files[0]);
      console.log(url);
      this.imageUrl = url;
      this.tabState = 1;
    },
    loadContent() {
      axios
        .get(
          this.posts.length == 3
            ? "https://codingapple1.github.io/vue/more0.json"
            : "https://codingapple1.github.io/vue/more1.json"
        )
        .then((res) => {
          this.posts.push(res.data);
        })
        .catch((err) => {
          alert(`Error fetching data!\n${err}`);
        });
    },
  },
};
</script>

<style>
body {
  margin: 0;
}
ul {
  padding: 5px;
  list-style-type: none;
}
.logo {
  width: 22px;
  margin: auto;
  display: block;
  position: absolute;
  left: 0;
  right: 0;
  top: 13px;
}
.header {
  width: 100%;
  height: 40px;
  background-color: white;
  padding-bottom: 8px;
  position: sticky;
  top: 0;
}
.header-button-left {
  color: skyblue;
  float: left;
  width: 50px;
  padding-left: 20px;
  cursor: pointer;
  margin-top: 10px;
}
.header-button-right {
  color: skyblue;
  float: right;
  width: 50px;
  cursor: pointer;
  margin-top: 10px;
}
.footer {
  width: 100%;
  position: sticky;
  bottom: 0;
  padding-bottom: 10px;
  background-color: white;
}
.footer-button-plus {
  width: 80px;
  margin: auto;
  text-align: center;
  cursor: pointer;
  font-size: 24px;
  padding-top: 12px;
}
.sample-box {
  width: 100%;
  height: 600px;
  background-color: bisque;
}
.inputfile {
  display: none;
}
.input-plus {
  cursor: pointer;
}
#app {
  box-sizing: border-box;
  font-family: "consolas";
  margin-top: 60px;
  width: 100%;
  max-width: 460px;
  margin: auto;
  position: relative;
  border-right: 1px solid #eee;
  border-left: 1px solid #eee;
}
</style>
