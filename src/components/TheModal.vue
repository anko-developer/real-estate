<template>
  <div v-if="modalState" class="black-bg">
    <div class="modal">
      <h4>{{ productsItem[modalId].title }}</h4>
      <p>{{ productsItem[modalId].content }}</p>
      <p>{{ productsItem[modalId].price }}원</p>
      <button @click="modalToggle()">닫기</button>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';
defineProps({
  productsItem: Array,
  modalId: Number,
  modalState: Boolean,
});
</script>

<style lang="scss" scoped>
.black-bg {
  width: 100%; height:100%;
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}
.modal {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
} 
</style>