<template>
  <div>
    <img :src="item.image" alt="" class="room-img">
    <!-- <h4 @click="modalToggle(index)">{{ item.title }}</h4> -->
    <p>{{ item.price }}만원</p>
    <p>{{ item.content }}</p>
    <!-- <button @click="reportPlus(item)">허위매물신고</button> -->
    <span>신고수: {{ item.report }}</span>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';

defineProps({
  item: Object,
  // modalId: Number,
  // modalState: Boolean,
});

// const modalId = ref(null);
// const modalState = ref(false);
// const reportPlus = (item) => {
//   item.report = ++item.report;
// };

// const modalToggle = (i = '') => {
//     modalState.value = !modalState.value;
//     modalId.value = i;
// };
</script>

<style lang="scss" scoped>

</style>