<template>
   <!--DEVELOPER - VINICIUS RICARDO MARTINS
    Email: martinsrvinicius@gmail.com
    -->
  <main>
    <button @click="toggle" v-if="code==1">Go to CSS Problem</button>
    <!--COIN PROBLEM COMPONENT-->
  <div v-if="code ==1">
  <CoinProblem />
  </div>
<!--CSS PROBLEM COMPONENT-->
  <div v-if="code==2">
    <CSSProblemView @toggle="toggle"/>
  </div>
</main>
</template>

<script setup lang="ts">
import CoinProblem from './components/CoinProblemView.vue'
import CSSProblemView from './components/CssProblemView.vue'
import {ref} from 'vue'

const code = ref(1)
function toggle() {
  if(code.value == 1){
    code.value = 2
  } else {
    code.value = 1
  }
}

</script>

<style >
:root {
  background-color: #5ba68a;
}

</style>