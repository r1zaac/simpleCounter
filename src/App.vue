<template>
  <div class="home">
    <h2>{{ appTitle }}</h2>

    <h3>{{ counterData.title }}:</h3>

    <div>
      <button @click="decreaseTwoCounter(2)" class="btn">-2</button>
      <button @click="decreaseCounter" class="btn">-</button>
      <span class="counter">{{ counterData.count }}</span>
      <button @click="increaseCounter" class="btn">+</button>
      <button @click="increaseTwoCounter(2)" class="btn">+2</button>
    </div>

    <p>The count number is {{ oddOrEven }}</p>
  </div>
</template>

<script setup>
import { reactive, computed } from "vue";

const appTitle = "My Amazing Counter App";

const counterData = reactive({
  count: 0,
  title: "Counter",
});

const oddOrEven = computed(() => {
  if (counterData.count % 2 === 0) return "Even";
  return "Odd";
});

const increaseCounter = () => {
  counterData.count++;
};

const increaseTwoCounter = (amount) => {
  counterData.count += amount;
};

const decreaseCounter = () => {
  counterData.count--;
  if (counterData.count < 0) {
    alert("Count cant be below 0");
    counterData.count = 0;
  }
};

const decreaseTwoCounter = (amount) => {
  counterData.count -= amount;
  if (counterData.count < 0) {
    alert("Count cant be below 0");
    counterData.count = 0;
  }
};
</script>

<style>
.home {
  text-align: center;
  padding: 20px;
}
.btn,
.counter {
  font-size: 40px;
  margin: 10px;
}
</style>
