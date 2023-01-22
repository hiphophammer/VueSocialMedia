<template>
  <img :src="room.image" class="image" />
  <h4 @click="$emit('openModal', room.id)">
    {{ room.title }}
  </h4>
  <p>{{ room.price + " 원" }}</p>
</template>

<script>
export default {
  name: "RoomCell",
  props: {
    room: Object,
  },
};
</script>

<style>
.image {
  width: 30rem;
  height: 15rem;
}
</style>
