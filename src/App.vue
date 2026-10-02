<script setup>
import { ref, computed } from 'vue';
const name = " Vue dinamico"

const increment = () => {
  console.log('aumentar contador')
  counter.value ++;
}
const counter =ref(0);

const decrement = () => {
  counter.value --;
}

const reset = () => {
  counter.value = 0;
}

const add = () => {
  arrayNum.value.push(counter.value)
}

const bloquearbtnAdd = computed (() =>{
  const numSearch = arrayNum.value.find(num => num === counter.value)
  console.log(numSearch);
  if(numSearch === 0) return true;
  return numSearch ? true : false;
})

const classcounter = computed(() => {
  if(counter.value === 0){
    return 'zero'
  }
  if(counter.value > 0){
    return 'positive'
  }
  if(counter.value < 0){
    return 'negative'
  }
})

const arrayNum = ref([]);

</script>

<template>
<div class="container text-center mt-5">
        <h1>Hola {{ name }}!</h1>
        <h2 :class="classCounter">
            {{ counter }}
        </h2>

        <div class="btn-group">
            <button @click="increment" class="btn btn-success">Incremet</button>
            <button @click="decrement" class="btn btn-danger">Decrement</button>
            <button @click="reset" class="btn btn-secondary">Reset</button>
            <button
                @click="add"
                :disabled="bloquearbtnAdd"
                class="btn btn-primary"
            >
                Add
            </button>
        </div>
        <ul class="list-group mt-2">
          <li class="list-group-item"
          v-for="(num, index) in arrayNum"
          :key="index"
          >
          {{ num }}
          </li>
        </ul>
</div>
</template>

<style>
h1{
  color:red
}
.positive {
  color:green;
}
.negative{
  color:red;
}
.zero{
  color: yellow;
}
</style>