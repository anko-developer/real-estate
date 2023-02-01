<template>
  <div v-if="modalState" class="black-bg">
    <div class="modal">
      <h4>타이틀</h4>
      <p>내용</p>
      <button @click="modalToggle">닫기</button>
    </div>
    
  </div>
  <nav class="menu">
    <a v-for="(item, index) in menuItems" :key="index" href="#">{{ item }}</a>
  </nav>

  <h1>원룸샵</h1>
  <div v-for="item in productsItem" :key="item.id">
    <img :src="item.image" alt="" class="room-img">
    <h4>{{ item.title }}</h4>
    <p>{{ item.price }}만원</p>
    <p>{{ item.content }}</p>
    <button @click="reportPlus(item)">허위매물신고</button>
    <span>신고수: {{ item.report }}</span>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue';
import { vuedongsan }  from '@/api';
const productsItem = reactive(vuedongsan);

const menuItems = reactive([
  'Home',
  'Products',
  'About',
]);

const reportPlus = (item) => {
  item.report = ++item.report;
};

const modalState = ref(true);
const modalToggle = () => {
    modalState.value = !modalState.value;
};
</script>

<style lang="scss" scoped>
body {
  margin : 0;
}
div {
  box-sizing: border-box;
}
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

.menu {
  background : darkslateblue;
  padding : 15px;
  border-radius : 5px;
}
.menu a {
  color : white;
  padding : 10px;
}

.room-img {
  width: 100%;
  margin-top: 40px;
}
</style>