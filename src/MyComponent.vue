<script setup>
import { ref } from 'vue';
const innerVariable=ref()
</script>

<template>
    <div>
        MyComponent
        <input type="text" 
        v-model="innerVariable"
        :on-change="$emit('ChangeValue',innerVariable)"
        >
    </div>
</template>