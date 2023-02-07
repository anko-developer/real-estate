<template>
  <div>
    <nav class="menu">
      <a v-for="(item, index) in menuItems" :key="index" href="#">{{ item }}</a>
    </nav>
    <TheModal :modalState="modalState" :productsItem="productsItem" :modalId="modalId" />
    <DiscountWord />

    <h1>원룸샵</h1>
    <TheCard :item="item" v-for="(item, index) in productsItem" :key="index" />
    <!-- <div v-for="(item, index) in productsItem" :key="index">
      <img :src="item.image" alt="" class="room-img">
      <h4 @click="modalToggle(index)">{{ item.title }}</h4>
      <p>{{ item.price }}만원</p>
      <p>{{ item.content }}</p>
      <button @click="reportPlus(item)">허위매물신고</button>
      <span>신고수: {{ item.report }}</span>
    </div> -->
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue';
import { vuedongsan }  from '@/api';
import DiscountWord from '@/components/DiscountWord.vue';
import TheModal from '@/components/TheModal.vue';
import TheCard from '@/components/TheCard.vue';
const productsItem = reactive(vuedongsan);

const menuItems = reactive([
  'Home',
  'Products',
  'About',
]);

const modalId = ref(null);
const modalState = ref(false);
</script>

<style lang="scss" scoped>
body {
  margin : 0;
}
div {
  box-sizing: border-box;
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