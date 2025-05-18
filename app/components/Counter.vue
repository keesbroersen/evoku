<script setup lang="ts">
const count = ref(0);

const increment = () => {
  count.value++;
};

const decrement = () => {
  count.value--;
};
</script>

<template>
  <div>
    <h3>Counter: {{ count }}</h3>
    <UButton @click="increment"> Increment </UButton>
    <UButton @click="decrement"> Decrement </UButton>
  </div>
</template>
