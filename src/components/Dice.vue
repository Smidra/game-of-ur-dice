<script>
export default {
  name: "test",
  props: ["rollResult", "shaking"],
}
</script>

<template>
  <img :class="{ shake: shaking }" v-if="rollResult === 1" class="w-1/2" src="../assets/kostka1.svg" alt="dice1">
  <img :class="{ shake: shaking }" v-if="rollResult === 2" class="w-1/2" src="../assets/kostka2.svg" alt="dice2">
  <img :class="{ shake: shaking }" v-if="rollResult === 3" class="w-1/2" src="../assets/kostka3.svg" alt="dice3">
  <img :class="{ shake: shaking }" v-if="rollResult === 4" class="w-1/2" src="../assets/kostka4.svg" alt="dice4">
  <img :class="{ shake: shaking }" v-if="rollResult === 5" class="w-1/2" src="../assets/kostka5.svg" alt="dice5">
  <img :class="{ shake: shaking }" v-if="rollResult === 6" class="w-1/2" src="../assets/kostka6.svg" alt="dice6">
</template>

<style scoped>
.shake {
  animation: shake 0.82s cubic-bezier(0.36, 0.07, 0.19, 0.97) both;
  transform: translate3d(0, 0, 0);
}

@keyframes shake {
  10%,
  90% {
    transform: translate3d(-1px, 0, 0);
  }

  20%,
  80% {
    transform: translate3d(2px, 0, 0);
  }

  30%,
  50%,
  70% {
    transform: translate3d(-4px, 0, 0);
  }

  40%,
  60% {
    transform: translate3d(4px, 0, 0);
  }
}
</style>