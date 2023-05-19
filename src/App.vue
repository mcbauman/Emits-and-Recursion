<script setup>
import { ref } from "vue";
import QRCodeVue3 from "qrcode-vue3"
import MyComponent from "./MyComponent.vue";
import BaseOutput from "./BaseOutput.vue"

let defaultVal = [
  {
    name: "Matthias",
    child: [
      { name: "Elodie", child: "not yet" },
      { name: "Torge", child: "not yet" }
    ]
  },
  {
    name: "Cynthia",
    child: "not yet"
  }
]

const myVariable = ref();
const myVar2=ref(defaultVal)
const myVar3=ref()

function submitFunction(){
  console.log(myVar2.value);
  myVar3.value=myVar2.value
}
</script>

<template>
     <!-- <QRCodeVue3
          value="http://jepleting.de"
        /> -->
  <header>
    World of Emits {{ myVariable }}
    <MyComponent @ChangeValue="(v) => (myVariable = v)" />
  </header>
  <main>
    <BaseOutput v-for="value in myVar2" :inputValue="value" />
    <button @click="submitFunction">Store</button>
    <div>
      {{ myVar3 }}
    </div>
  </main>
</template>

<style>
body{
  background-color: rgb(224, 224, 224);
  font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
}
#app{
  max-width: 1200px;
  margin:0 auto;
}
</style>
