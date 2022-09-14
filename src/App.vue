<script setup>
import { ref, computed } from "vue";

const name = "Vue 3";

// counter ahora es una variable reactiva
const counter = ref(0);
const arrNum = ref([]);

const increment = () => {
  // mutamos el valor a través de .value
  counter.value++;
};

const decrement = () => {
  // mutamos el valor a través de .value
  counter.value--;
};

const restart = () => {
  // mutamos el valor a través de .value
  counter.value = 0;
};

const add = () => {
  // mutamos el valor a través de .value
  arrNum.value.push(counter.value);
};

const classCounter = computed(() => {
  if (counter.value === 0) {
    return 'zero'
  }
  if (counter.value > 0) {
    return 'positive'
  }
  if (counter.value < 0) {
    return 'negative'
  }
})

const btnAdd = computed(() => {
  const numSearch = arrNum.value.find(num => num === counter.value);

  return numSearch || numSearch === 0;
})
</script>

<template>
  <div class="container">
    <h1>Hi {{ name }}!</h1>
    <h2 :class="classCounter">
      {{ counter }}
    </h2>

    <div class="btn-group">
      <button class="btn btn-success" @click="increment">Click incremet</button>
      <button class="btn btn-danger" @click="decrement">Click decrement</button>
      <button class="btn btn-secondary" @click="restart">Click restart</button>
      <button class="btn btn-primary" @click="add" :disabled="btnAdd">
        Add
      </button>
    </div>
    
    <ul class="list-group mt-4">
      <li class="list-group-item" v-for="(num, index) in arrNum" :key="index">
        {{ num }}
      </li>
    </ul>
  </div>
</template>

<style>
  .negative {
    color: red;
  }
  .positive {
    color: green;
  }
  .zero {
    color: peru;
  }
</style>