<script setup>
import { ref } from "vue";
import QRCodeVue3 from "qrcode-vue3"
import MyComponent from "./MyComponent.vue";
import BaseOutput from "./BaseOutput.vue"
import BaseOutput2 from "./BaseOutput2.vue"

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
//FOR ASIDE
const structure = ref(defaultVal)
const newValues=ref()



//FOR MAIN
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
  
  <!-- <aside>
    <BaseOutput2 v-for="structureItem in structure" 
      :structureItem="structureItem"
      :inputValue="newValues"
      v-model="newValues"
    /> 
  </aside> -->
  
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
