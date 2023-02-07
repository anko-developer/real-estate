<template>
  <div>
    <nav class="menu">
      <a v-for="(item, index) in menuItems" :key="index" href="#">{{ item }}</a>
    </nav>
    <Transition name="fade">
      <TheModal @modalClose="modalState = $event" :modalState="modalState" :productsItem="productsCopyItem" :modalId="modalId" />
    </Transition>
    <DiscountWord />

    <button @click="priceSort">가격순정렬</button>
    <button @click="titleSort">제목순정렬</button>

    <h1>원룸샵</h1>
    <TheCard @openModal="modalData($event)" :item="item" v-for="(item, index) in productsCopyItem" :key="index" />
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue';
import { vuedongsan }  from '@/api';
import DiscountWord from '@/components/DiscountWord.vue';
import TheModal from '@/components/TheModal.vue';
import TheCard from '@/components/TheCard.vue';

const productsItem = reactive(vuedongsan);
const productsCopyItem = reactive([...productsItem]);

const menuItems = reactive([
  'Home',
  'Products',
  'About',
]);

const modalId = ref(null);
const modalState = ref(false);
const modalData = (id) => {
  modalState.value = true;
  modalId.value = id;
};

const priceSort = () => {
  // sort는 원본을 변형 시켜버림
  productsCopyItem.sort((a, b) => {
    return a.price - b.price;
  });
};

const compare = (title) => {
  return (a, b) => (a[title] > b[title] ? 1 : (a[title] < b[title]  ? -1 : 0));
};
const titleSort = () => {
  productsCopyItem.sort(compare('title'));
  console.log('되돌린다.', productsCopyItem);
};
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

// transition
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>