<script>
export default {
  name: "test",
  props: ["rollResult", "shaking"],
}
</script>

<template>
  <img :class="{ shake: shaking }" v-if="rollResult === 1" class="w-full" src="../assets/kostka1.svg">
  <img :class="{ shake: shaking }" v-if="rollResult === 2" class="w-full" src="../assets/kostka2.svg">
  <img :class="{ shake: shaking }" v-if="rollResult === 3" class="w-full" src="../assets/kostka3.svg">
  <img :class="{ shake: shaking }" v-if="rollResult === 4" class="w-full" src="../assets/kostka4.svg">
  <img :class="{ shake: shaking }" v-if="rollResult === 5" class="w-full" src="../assets/kostka5.svg">
  <img :class="{ shake: shaking }" v-if="rollResult === 6" class="w-full" src="../assets/kostka6.svg">
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