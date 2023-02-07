<template>
  <div v-if="modalState" class="black-bg">
    <div class="modal">
      <h4>{{ productsItem[modalId].title }}</h4>
      <p>{{ productsItem[modalId].content }}</p>
      <input v-model="month" type="text">
      <select v-model="month" name="" id="">
        <option value="1">1</option>
        <option value="2">2</option>
        <option value="3">3</option>
      </select>
      <p>{{ month }} 개월 선택함: {{ productsItem[modalId].price * month }}원</p>
      <button @click="modalClose">닫기</button>
    </div>
  </div>
</template>

<script setup>
import { defineProps, defineEmits, ref, watch } from 'vue';

defineProps({
  productsItem: Array,
  modalId: Number,
  modalState: Boolean,
});

const month = ref(1);
const emit = defineEmits(['modalClose']);
const modalClose = () => {
  emit('modalClose', false);
};

watch(month, (a) => { // a는 변경 후 데이터, b는 변경 전 데이터
  if (isNaN(a)) {
    month.value = 1;
    console.log('숫자가 아니잖아?');
  }
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