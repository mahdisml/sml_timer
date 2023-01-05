<script setup>
import { ref , watch , reactive} from 'vue';

let state = ref(0)
let main = ref(0.0)
let secondary = ref(0.0)

setInterval(() => {
  if (state.value === 1){
    main.value = main.value + 0.0166666666667;
  }
  if (state.value === 2){
    secondary.value = secondary.value + 0.0166666666667;
  }
}, 1000);

function setState (a){
  state.value = a
}
function getSituation(a){
  switch(a){
    case 1: {
      if (state.value === 1){return true}else {return false}
    }
    case 2: {
      if (state.value === 2){return true}else {return false}
    }
    default: {
      if (state.value === 0){return true}else {return false}
    }
  }
}


</script>

<template>
  <div class=" w-screen h-screen">
    <div class="w-full h-full flex flex-col flex-nowrap justify-center items-center bg-[#191919]">
      <h1 class="text-white w-6/12 flex flex-row flex-nowrap justify-center items-center">
        <div class="w-6/12 flex flex-row justify-end items-center">
          Main Work : {{main.toFixed(2)}}
          <div class="w-20"></div>
        </div>
        <div class="w-6/12 flex flex-row justify-start items-center">
          <input type="checkbox" v-bind:checked="getSituation(1)" v-on:click="setState(1)"  class="toggle toggle-lg bg-black checked:bg-white"/>
         </div>
      </h1>
      <div class="h-10"/>
      <h1 class="text-white w-6/12 flex flex-row flex-nowrap justify-center items-center">
        <div class="w-6/12 flex flex-row justify-end items-center">
          Secondary Work  : {{secondary.toFixed(2)}}
          <div class="w-20"></div>
        </div>
        <div class="w-6/12 flex flex-row justify-start items-center">
          <input type="checkbox" v-bind:checked="getSituation(2)" v-on:click="setState(2)"   class="toggle toggle-lg bg-black checked:bg-white"/>
        </div>
      </h1>
      <div class="h-10"/>
      <h1 class="text-white w-6/12 flex flex-row flex-nowrap justify-center items-center">
        <div class="w-6/12 flex flex-row justify-end items-center">
          None
          <div class="w-20"></div>
        </div>
        <div class="w-6/12 flex flex-row justify-start items-center">
          <input type="checkbox" v-bind:checked="getSituation(0)" v-on:click="setState(0)"  class="toggle toggle-lg bg-black checked:bg-white"/>
        </div>
      </h1>
    </div>
  </div>
</template>
