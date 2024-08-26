/* eslint-disable */
// Reactivity with the ref() Method
<!-- <template>
    <div>
        <h1 class="red-text"> My Counter Component </h1>
        <h2>Reactive variable count: {{ count }}</h2>
        <h2>Computed variable Double Count: {{ doubleCount }}</h2>
        <br />
        <button @click="start()">Start</button>
        <button @click="stop()">Stop</button>
        <button @click="increment()">Increment</button>
        <button @click="count--">Decrement</button>
    </div>
</template> -->

<template>
    <div>
        <h1> Reactuve Variable count : {{ count }}</h1>
        <br />
        <button @click="increment()"> Increment </button>
    </div>
</template>

<script setup>
    import { customRef } from 'vue';
    // creating a custom ref variable 
    const count = customRef((track, trigger) => {
        let value = 0;
        return {
            get(){
                // Track the dependency
                track();
                console.log("get value : ", value);
                return value;
            },
            set(newValue){
                // update the value and trigger
                value = newValue;
                trigger();
                console.log("set value = ", value);
            }
        }
    })
    
    // click event handler
    function increment() {
        console.log('Before Increment')
        count.value += 1;
        console.log("After Increment");
    }
</script>

<!-- <script setup>
    import { computed, onMounted, onUnmounted, ref } from 'vue';

    let timer;
    const count = ref(0);
    const increment = () => count.value++;
    // Computed Propertied
    const doubleCount = computed(() => count.value * 2)

    const start = () => {timer = setInterval(() => increment(), 2000)}
    const stop = () => {clearInterval(timer)}
    onMounted(() => start())
    onUnmounted(() => stop())
</script> -->

<!-- <script setup>
    import { computed, onBeforeMount, onBeforeUnmount, onBeforeUpdate, onMounted, onUnmounted, onUpdated, ref } from 'vue'
    // Creating a reactive variable count with an initial value of 0
    const count = ref(0);
    function increment() {
        count.value++;
    }

    // Computed Properties
    const doubleCount = computed(function() {
        return count.value * 2;
    })

    console.log("Setup : The component is created in memory.");
    // Life cycle methods
    onBeforeMount(() => { console.log("Before Mount : The component is about to be mounted on the DOM") })
    onMounted(() => { console.log("On Mounting : The component has been mounted on the DOM") })
    onBeforeUpdate(() => { console.log("On Before Update : The component is about to be updated on the DOM") })
    onUpdated(() => { console.log("On Updated : The component has been updated on the DOM") })
    onBeforeUnmount(() => { console.log("On Before Unmounted : The component is about to be unmounted") })
    onUnmounted(() => { console.log("On Unmounted : The component has been unmounted") })
</script> -->

<!-- <script>
export default{
    name: 'MyCounter',
}
</script> -->
<!-- <script>
import { defineComponent } from "@vue/composition-api";

export default defineComponent({
    setup() {
        
    },
})
</script> -->

<style scoped>
    .red-text{
        color: red;
    }
</style>

<!-- 
Life clycle methods in Vue Component 
setup: Included in the script. It is executed only once during the creation of the component in memory.
onMounted(callbackfn)
unUpdated(callbackfn)
onUnmounted(callbackfn)
These methods exist to perform processing before it is realised
onBeforeMount(callbackfn)
onBeforeUpdate(callbackfn)
onBeforeUnmount(callbackfn)
-->