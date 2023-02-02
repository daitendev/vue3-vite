<script setup lang="ts">
import { ref, reactive } from 'vue'
const itemName1 = ref<string>('desk')
const itemName2 = 'bike'

const item1 = reactive(
  {
    name: 'desk',
    price: 40000
  }
)

const buy = (itemName: string) => {
  alert('Are you sure to buy?' + itemName)
}

const input = (event: any) => {
  item1.name = event.target.value
}
const inputPrice = (event: any) => {
  item1.price = event.target.value
}
</script>

<template>
  <div class="container">
    <h1>Payment</h1>
    <input v-on:input="input">
    <input v-on:input="inputPrice">
    <div class="payment">
      <label>{{ item1.name }}</label>
      <label>{{ item1.price }} yen</label>
      <button v-on:click="buy(item1.name)">BUY</button>
    </div>
    <div class="payment">
      <label>{{ itemName2 }}</label>
      <label>400円</label>
      <button v-on:click="buy(itemName2)">BUY</button>
    </div>
  </div>
</template>

<style scoped>
label {
  font-size: 20px;
  font-weight: 700;
}

.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.payment {
  display: flex;
  justify-content: space-between;
  height: 80px;
  width: 400px;
  color: black;
  background-color: aliceblue;
  margin-bottom: 50px;
}
</style>