Coin Problem
============

Part 1
------

You are given any amount of money in the format X.XX (f.e. `2.34`). 

Implement a function that split this amount in the minimal amount of Euro coins, which represents the given number.

The Euro coins are:

2€, 1€, 50¢, 20¢, 10¢, 5¢, 2¢, 1¢

Example:
Given the amount of 2.34 the result will be `[ 2, 0.2, 0.02, 0.1, 0.02 ]`

Please implement this function.

# RESPONSE

# A Vue framework solution
<template>
     <!--DEVELOPER - VINICIUS RICARDO MARTINS
    Email: martinsrvinicius@gmail.com
    -->
    <div>
        <h1> Part 1</h1>
        ------
        <p>You are given any amount of money in the format X.XX (f.e. `2.34`).

            Implement a function that split this amount in the minimal amount of Euro coins, which represents the given
            number.

            The Euro coins are:

            2€, 1€, 50¢, 20¢, 10¢, 5¢, 2¢, 1¢

            Example:
            Given the amount of 2.34 the result will be `[ 2, 0.2, 0.02, 0.1, 0.02 ]`

            Please implement this function.
        </p>
    </div>
    <!--INPUT FOR VALIDATION FUNCTION-->
    <input type="number" v-model="amount">
    <div v-for="(item, index) in coins" :key="index">
        coins: {{ item }}€
    </div>
</template>
<script setup lang="ts">
import { ref, onMounted, watch } from 'vue'

const coins = ref([])
const amount = ref(2.34)

onMounted(() => {
    formula(amount.value)
})
//a watcher for the input amount so the function might update the view
watch(amount, () => {
    formula(amount.value)
})

//Function that receives the amount to split into coins
function formula(value: number) {
    coins.value = []
    let temp = ''
    let total = 0
    //Loop through the value while it is greater than 0
    do {
        //if value is higher or equals to 2 choose €2 coin
        if (value >= 2) {
            // mod value into variable total to have the a control during the test
            total += value % 2
            //€2 coin used is added into the array that will be printed
            coins.value.push(2)
            //€2 subtracted from the total amount variable so the loop might stop
            value -= 2
            //result into a temporary variable to keep the value with only 2 digits
            temp = value.toFixed(2)
            //temp is parsed to a number and goes back to the amount with only 2 digits
            value = Number(temp)
        }
        //same logic above and test the value if value > 1 and value <2
        if (value < 2 && value == 1) {
            total += value % 1
            coins.value.push(1)
            value -= 1
            temp = value.toFixed(2)
            value = Number(temp)
        }
        if (value < 1 && value >= 0.5) {
            total += value % 0.5
            coins.value.push(0.5)
            value -= 0.5
            temp = value.toFixed(2)
            value = Number(temp)
        }
        if (value < 0.5 && value >= 0.2) {
            total += value % 0.2
            coins.value.push(0.2)
            value -= 0.2
            temp = value.toFixed(2)
            value = Number(temp)
        }
        if (value < 0.2 && value >= 0.1) {
            total += value % 0.1
            value -= 0.1
            coins.value.push(0.1)
            temp = value.toFixed(2)
            value = Number(temp)
        }
        if (value < 0.1 && value >= 0.05) {
            total += value % 0.05
            value -= 0.05
            coins.value.push(0.05)
            temp = value.toFixed(2)
            value = Number(temp)
        }
        if (value < 0.05 && value >= 0.02) {
            total += value % 0.02
            value -= 0.02
            coins.value.push(0.02)
            temp = value.toFixed(2)
            value = Number(temp)
        }
        if (value < 0.02 && value >= 0.01) {
            total += value % 0.01
            value -= 0.01
            coins.value.push(0.01)
            temp = value.toFixed(2)
            value = Number(temp)
        }
        //stops the loop
    } while (value >= 0.01)
}

</script>
