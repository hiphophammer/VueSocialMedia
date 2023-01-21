<template>
  <div class="black-bg" v-if="modalNumber > -1">
    <div class="white-bg">
      <h4>{{ rooms[modalNumber].title }}</h4>
      <p>{{ rooms[modalNumber].content }}</p>
      <button @click="modalNumber = -1">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "ModalComp",
};
</script>

<style>
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
</style>
