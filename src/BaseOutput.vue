<script setup>
const props=defineProps(["inputValue"])

console.log(props.inputValue);
</script>

<template>
    <section>
        <span>Name:</span>
        <input type="text" v-model="props.inputValue.name">
        <hr>
        <span>Children:</span>
        <h3 v-if="props.inputValue.child=='not yet'">{{props.inputValue.child}}</h3>
        <BaseOutput v-else v-for="childOfInputVal in props.inputValue.child" :inputValue="childOfInputVal" />
    </section>
</template>

<style scoped>
section{
    border-radius: 5px;
    padding: 10px;
    margin:10px;
    box-shadow: 0 0 6px 1px rgb(165, 23, 23);
    background-color: rgba(128, 128, 128, 0.5);
}
span{
    font-size: small;
}
h3{
    display: inline;
    margin:0;
    padding: 0;
}
</style>