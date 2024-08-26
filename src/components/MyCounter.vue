<template>
<div>

    <h1 class="red-text">My Counter Component</h1>
    <h2>{{count}}</h2>
    <b> {{  doubleCount}}</b>
    <br/><br/>
    <button @click="increment()"> Increment</button>
    <button @click="count--"> Decrement</button>
</div>
</template>
<script setup>
import {computed ,ref} from 'vue';
const count =ref(10);
function increment(){
    count.value++;
}

const doubleCount = computed(function() {
    return count.value * 2;
})

</script>
<style scoped>
.red-text {
    color:red
}
</style>