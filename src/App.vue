<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <HelloWorld @search="onSearch1" v-model="leftSearch1" />
    <span>v-model value in parent: {{ leftSearch1 }}</span>
    <HelloWorld @search="onSearch2" :value="leftSearch2" @update:value="leftSearch2 = $event"  />
    <span>v-model value in parent: {{ leftSearch2 }}</span>
    <HelloWorld @search="onSearch3" :modelValue="leftSearch3" @update:modelValue="leftSearch3 = $event" />
    <span>v-model value in parent: {{ leftSearch3 }}</span>
  </div>
</template>

<script lang="ts" setup>
import { ref } from "vue";
import HelloWorld from "./components/HelloWorld.vue";

const leftSearch1 = ref("");
const leftSearch2 = ref("");
const leftSearch3 = ref("");


function onSearch1(val?: string) {
  console.log(val, leftSearch1.value);
}

function onSearch2(val?: string) {
  console.log(val, leftSearch2.value);
}

function onSearch3(val?: string) {
  console.log(val, leftSearch3.value);
}

</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
