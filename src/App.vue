<template>
  <div>
    <input type="text" class="calculator__display" v-model="display" disabled />
    <div class="calculator__buttons">
      <button class="calculator__button" @click="appendToDisplay('7')">7</button>
      <button class="calculator__button" @click="appendToDisplay('8')">8</button>
      <button class="calculator__button" @click="appendToDisplay('9')">9</button>
      <button class="calculator__button" @click="appendToDisplay('+')">+</button>
      <button class="calculator__button" @click="appendToDisplay('4')">4</button>
      <button class="calculator__button" @click="appendToDisplay('5')">5</button>
      <button class="calculator__button" @click="appendToDisplay('6')">6</button>
      <button class="calculator__button" @click="appendToDisplay('-')">-</button>
      <button class="calculator__button" @click="appendToDisplay('1')">1</button>
      <button class="calculator__button" @click="appendToDisplay('2')">2</button>
      <button class="calculator__button" @click="appendToDisplay('3')">3</button>
      <button class="calculator__button" @click="appendToDisplay('*')">&times;</button>
      <button class="calculator__button" @click="appendToDisplay('0')">0</button>
      <button class="calculator__button" @click="appendToDisplay('.')">.</button>
      <button class="calculator__button" @click="calculate()">=</button>
      <button class="calculator__button" @click="clear()">C</button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const display = ref('')

const appendToDisplay = (value: string) => {
  display.value += value
}

const calculate = () => {
  try {
    display.value = eval(display.value).toString()
  } catch (error) {
    display.value = 'Error'
  }
}

const clear = () => {
  display.value = ''
}
</script>

<style scoped>
.calculator__display {
  font-size: 2em;
  text-align: right;
  border: none;
  background-color: transparent;
  width: 100%;
  margin-bottom: 10px;
  padding-right: 10px;
  height: 60px;
}

.calculator__buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px;
}

.calculator__button {
  border: none;
  outline: none;
  padding: 15px;
  border-radius: 5px;
  font-size: 1.5em;
  cursor: pointer;
  background-color: #ededed;
}

.calculator__button:hover {
  background-color: #dcdcdc;
}
</style>
