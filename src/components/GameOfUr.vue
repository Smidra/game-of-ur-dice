<script>
import {Card, CardHeader, CardTitle, CardDescription, CardFooter, CardContent} from "@/components/ui/card/index.js";
import {Button} from "@/components/ui/button/index.js";
import Dice from "@/components/Dice.vue";

export default {
  name: "GameOfUr",
  components: {Dice, Card, CardHeader, CardTitle, CardDescription, CardFooter, Button, CardContent},
  data() {
    return {
      dices: [1, 1, 1, 1],
      dicesShaking: [false, false, false, false],
      timeoutMin: 50,
      timeoutMax: 200,
      flashRepeat: 7
    }
  },
  methods: {
    randomInt(min, max) {
      const minCeiled = Math.ceil(min);
      const maxFloored = Math.floor(max);
      return Math.floor(Math.random() * (maxFloored - minCeiled) + minCeiled); // The maximum is exclusive and the minimum is inclusive
    },
    async randomizeDiceForTime(diceNumber) {
      this.dicesShaking[diceNumber] = true
      for (let i = 0; i < this.flashRepeat; i++) {
        this.dices[diceNumber] = this.randomInt(1, 6)
        await new Promise(resolve => setTimeout(resolve, this.randomInt(this.timeoutMin, this.timeoutMax)));
      }
      this.dicesShaking[diceNumber] = false
      this.dices[diceNumber] = this.randomInt(1, 6)
      await new Promise(resolve => setTimeout(resolve, this.randomInt(this.timeoutMax, this.timeoutMax)));
      this.dices[diceNumber] = this.randomInt(1, 6)
    },
    rollMethod() {
      var audio = new Audio('http://soundbible.com/grab.php?id=182&type=mp3');
      audio.play();
      this.randomizeDiceForTime(0)
      this.randomizeDiceForTime(1)
      this.randomizeDiceForTime(2)
      this.randomizeDiceForTime(3)
    }
  }
}
</script>

<template>
  <card class="m-5 w-full sm:w-3/5 md:w-2/5 lg:w-1/5">
    <CardHeader>
      <CardTitle>Game of Ur dice online</CardTitle>
      <CardDescription>The royal game of Ur dice online simulator free.</CardDescription>
    </CardHeader>

    <CardContent>
      <div class="grid items-center w-full gap-4">
        <div class="flex flex-row justify-between">
          <dice :roll-result="dices[0]" :shaking="dicesShaking[0]"></dice>
          <dice :roll-result="dices[1]" :shaking="dicesShaking[1]"></dice>
        </div>
        <div class="flex flex-row justify-between">
          <dice :roll-result="dices[2]" :shaking="dicesShaking[2]"></dice>
          <dice :roll-result="dices[3]" :shaking="dicesShaking[3]"></dice>
        </div>
      </div>
    </CardContent>

    <CardFooter class="w-full px-6 pb-6">
      <Button class="w-full" variant="outline" @click="rollMethod">Roll the dice!</Button>
    </CardFooter>
  </card>
</template>

<style scoped>

</style>