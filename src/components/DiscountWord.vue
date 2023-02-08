<template>
  <div class="discount">
    <h4>지금 결제하면 {{ discount }}% 할인</h4>
  </div>
</template>

<script setup>
import { defineProps } from 'vue';

defineProps({
  discount: String,
});
</script>

<style lang="scss" scoped>
.discount {
  margin: 10px;
  padding: 10px;
  border-radius: 5px;
  text-align: center;
  background-color: #EEE;
}
</style>