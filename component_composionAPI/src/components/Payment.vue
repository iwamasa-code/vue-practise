<script setup lang="ts">
import { ref, reactive } from 'vue';
const itemName2 = ref<string>('Bike');
const price2 = 20000;

const item1 = reactive({
  name: 'Desk',
  price: 40000,
});

const url1 = 'https://www.youtube.com/';
const url2 = 'https://www.amazon.co.jp/';

const buy = (itemName: string) => {
  alert('Are you sure to buy ' + itemName + '?');
};

//reactiveの場合
// const input = (event: any) => {
//   item1.name = event.target.value;
// };
// const inputPrice = (event: any) => {
//   item1.price = event.target.value;
// };

// refの場合
// const input = (event: any) => {
//   itemName2.value = event.target.value;
// };

const onClickClearButton = () => {
  item1.name = '';
  item1.price = 0;
};
</script>

<template>
  <div class="container">
    <h1>最近の支出</h1>
    <input placeholder="商品名" v-model="item1.name" />
    <input placeholder="金額" v-model="item1.price" />
    <button @click="onClickClearButton">クリア</button>
    <div class="payment">
      <label>{{ item1.name }}</label>
      <label>{{ item1.price }} yen</label>
      <a v-bind:href="url1">bought at...</a>
      <button v-on:click="buy(item1.name)">buy</button>
    </div>
    <div class="payment">
      <label>{{ itemName2 }}</label>
      <label>{{ price2 }} yen</label>
      <a v-bind:href="url2">bought at...</a>
      <button v-on:click="buy(itemName2)">buy</button>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.payment {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 80px;
  width: 400px;
  background-color: aliceblue;
  margin-bottom: 8px;
}

label {
  font-size: 20px;
  font-weight: bold;
}

input {
  margin-bottom: 8px;
}

button {
  margin-bottom: 8px;
}
</style>
