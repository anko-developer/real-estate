<template>
  <nav class="menu">
    <a v-for="(item, index) in menuItems" :key="index" href="#">{{ item }}</a>
  </nav>

  <h1>원룸샵</h1>
  <div v-for="(item, index) in products" :key="index">
    <h4>{{ item.name }}</h4>
    <p>{{ item.price }}만원</p>
    <button @click="reportPlus(item)">허위매물신고</button>
    <span>신고수: {{ item.report }}</span>
  </div>
</template>

<script setup>
import { reactive } from 'vue';

const menuItems = reactive([
  'Home',
  'Products',
  'About',
]);

const products = reactive([
  {
    name: '역삼동원룸',
    price: 70,
    report: 0,
  },
  {
    name: '천호동원룸',
    price: 50,
    report: 1,
  },
  {
    name: '마포구원룸',
    price: 100,
    report: 2,
  },
]);

// const errorCount = ref(0);
const reportPlus = (item) => {
  item.report = ++item.report;
};
</script>

<style lang="scss" scoped>
.menu {
  background : darkslateblue;
  padding : 15px;
  border-radius : 5px;
}
.menu a {
  color : white;
  padding : 10px;
}
</style>